### <a name="lxc">LXC</a>

LXC(Linux Container) resource type.

You can test LXC like this.

```ruby
describe lxc('ct01') do
  it { should exist }
  it { should be_running }
end
```

```ruby
describe lxc('ct01') do
  it "exists" do
    expect(subject).to exist
  end

  it "is running" do
    expect(subject).to be_running
  end
end
```
