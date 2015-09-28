---
layout: post
title: "Stubbing encrypted_data_bag_for_environment"
date: 2015-09-28 05:03:26 -0700
comments: true
categories: chef
---

We use the `encrypted_data_bag_for_environment` method from the [chef-sugar](https://github.com/sethvargo/chef-sugar) library pretty heavily in the cookbooks my team uses. With that said, I can never seem to remember the right invocation of stubs and mocks to be able to test recipes that have those calls in them. Since I don't want to have to come up with this again, here is an example of how I did it this morning. In this example, I am stubbing a data bag item that has creds for using DataDog.

```
require 'spec_helper'

describe 'cia_infra::base' do
  let(:chef_run) do
    stub_command('which sudo').and_return('/usr/bin/sudo')
    Chef::Config['encrypted_data_bag_secret'] = '/dev/null'
    @runner = ChefSpec::ServerRunner.new
    @runner.converge(described_recipe)
  end

  before do
    allow(Chef::EncryptedDataBagItem).to receive(:load).with('cia-creds', 'datadog', '').and_return({
      'default' => {
        'api_key' => 'datadog_api_key',
        'application_key' => 'datadog_application_key',
      }
    })
  end

  it { expect(chef_run).to include_recipe('apt') }
  it { expect(chef_run).to include_recipe('chef-client') }
  it { expect(chef_run).to include_recipe('chef-client::delete_validation') }
  it { expect(chef_run).to include_recipe('ntp') }
  it { expect(chef_run).to include_recipe('push-jobs') }
  it { expect(chef_run).to include_recipe('oc-users') }
  it { expect(chef_run).to include_recipe('cia_infra::monitoring') }
end
```

It is entirely possible that I am doing this wrong, but hey, it works. I would love to hear better approaches if there are any.
