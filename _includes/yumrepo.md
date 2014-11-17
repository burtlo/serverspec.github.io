### <a name="yumrepo">yumrepo</a>

Yumrepo resource type.

#### exist

In order to test a given yum repository exists,  you should use **exist** matcher.

```ruby
describe yumrepo('epel') do
  it { should exist }
end
```

```ruby
describe yumrepo('epel') do
  it "exists" do
    expect(subject).to exist
  end
end
```

#### be_enabled

In order to test a given yum repository is enabled,  you should use **be_enabled** matcher.

```ruby
describe yumrepo('epel') do
  it { should be_enabled }
end
```

```ruby
describe yumrepo('epel') do
  it "enabled" do
    expect(subject).to be_enabled
  end
end
```
