### <a name="host">host</a>

Host resource type.

#### be_resolvable

In order to test a host is resolvable on the target host, you should use **be_resolvable** matcher.

```ruby
describe host('serverspec.org') do
  it { should be_resolvable }
end

describe host('serverspec.org') do
  it { should be_resolvable.by('hosts') }
end

describe host('serverspec.org') do
  it { should be_resolvable.by('dns') }
end
```

```ruby
describe host('serverspec.org') do
  it "is resolvable" do
    expect(subject).to be_resolvable
  end
end

describe host('serverspec.org') do
  it "is resolvable by hosts" do
    expect(subject).to be_resolvable.by('hosts')
  end
end

describe host('serverspec.org') do
  it "is resolvable by dns" do
    expect(subject).to be_resolvable.by('dns')
  end
end
```

#### be_reachable

In order to test a given host is network reachable, you should use **be_reachable** matcher.

```ruby
describe host('target.example.jp') do
  # ping
  it { should be_reachable }
  # tcp port 22
  it { should be_reachable.with( :port => 22 ) }
  # set protocol explicitly
  it { should be_reachable.with( :port => 22, :proto => 'tcp' ) }
  # udp port 53
  it { should be_reachable.with( :port => 53, :proto => 'udp' ) }
  # timeout setting (default is 5 seconds)
  it { should be_reachable.with( :port => 22, :proto => 'tcp', :timeout => 1 ) }
end
```

```ruby
describe host('target.example.jp') do
  it "reachable" do
    expect(subject).to be_reachable
  end

  it "reachable on the default ssh port" do
    expect(subject).to be_reachable.with( :port => 22 )
  end

  it "reachable on the default ssh port with tcp protocol" do
    expect(subject).to be_reachable.with( :port => 22, :proto => 'tcp' )
  end

  it "reachable on port 53 with udp protocol" do
    expect(subject).to be_reachable.with( :port => 53, :proto => 'udp' )
  end

  it "reachable within a second" do
    expect(subject).to be_reachable.with( :port => 22, :proto => 'tcp', :timeout => 1 )
  end
end
```

#### its(:ipaddress)

You can get the ipaddress of the host,  and can use any matchers rspec supports to them.

```ruby
describe host('example.jp') do
  its(:ipaddress) { should eq '1.2.3.4' }
end

describe host('example.jp') do
  its(:ipaddress) { should match /1\.2\.3\./ }
end
```

```ruby
describe host('example.jp') do
  it "correct ipaddress" do
    expect(subject.ipaddress).to eq('1.2.3.4')
  end
end

describe host('example.jp') do
  it "correct ipaddress" do
    expect(subject.ipaddress).to match(/1\.2\.3\./)
  end
end
```
