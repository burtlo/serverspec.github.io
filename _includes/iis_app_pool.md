### <a name="iis_app_pool">iis\_app\_pool</a>

IIS Application Pool resource type.

#### exists

In order to test that an IIS app pool exists, you should use **exists** matcher.

```ruby
describe iis_app_pool('Default App Pool') do
  it{ should exist }
end
```

```ruby
describe iis_app_pool('Default App Pool') do
  it "exists" do
    expect(subject).to exist
  end
end
```

#### have\_dotnet\_version

In order to test that an IIS app pool is using the correct .NET version, you should use **have_dotnet_version** matcher.

```ruby
describe iis_app_pool('Default App Pool') do
  it{ should have_dotnet_version('2.0') }
end
```

```ruby
describe iis_app_pool('Default App Pool') do
  it "has the correct dotnet version" do
    expect(subject).to have_dotnet_version('2.0')
  end
end
```
