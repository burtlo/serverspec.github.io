### <a name="cgroup">cgroup</a>

Linux cgroup resource type.

You can test cgroup parameters like this.

```ruby
describe cgroup('group1') do
  its('cpuset.cpus') { should eq 1 }
end
```

```ruby
describe cgroup('group1') do
  it "cpuset has the correct number of cpus" do
    expect(subject.cpuset.cpus).to eq 1
  end
end
```
