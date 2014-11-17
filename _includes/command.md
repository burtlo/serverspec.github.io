### <a name="command">command</a>

Command resource type.

#### its(:stdout), its(:stderr), its(:exit_status)

You can get the stdout, stderr ane exit status of the command result, and can use any matchers RSpec supports.

```ruby
describe command('ls -al /') do
  its(:stdout) { should match /bin/ }
end

describe command('ls /foo') do
  its(:stderr) { should match /No such file or directory/ }
end

describe command('ls /foo') do
  its(:exit_status) { should eq 0 }
end
```

```ruby
describe command('ls -al /') do
  it "contains a bin in path" do
    expect(subject.stdout).to match(/bin/)
  end
end

describe command('ls /foo') do
  it "does not contain the path" do
    expect(subject.stderr).to match(/No such file or directory/)
  end
end

describe command('ls /foo') do
  it "executes without error" do
    expect(subject.exit_status).to eq 0
  end
end
```
