### <a name="port">port</a>

Port resource type.

#### be_listening

In order to test a given port is listening, you should use **be_listening** matcher.

```ruby
describe port(80) do
  it { should be_listening }
end
```

```ruby
describe port(80) do
  it "listening" do
    expect(subject).to be_listening
  end
end
```

You can also specify ``tcp``, ``udp``, ``tcp6``, or ``udp6``.


```ruby
describe port(80) do
  it { should be_listening.with('tcp') }
end

describe port(80) do
  it { should be_listening.with('tcp6') }
end

describe port(53) do
  it { should be_listening.with('udp') }
end

describe port(53) do
  it { should be_listening.with('udp6') }
end
```

```ruby
describe port(80) do
  it "listening with tcp" do
    expect(subject).to be_listening.with('tcp')
  end
end

describe port(80) do
  it "listening with tcp6" do
    expect(subject).to be_listening.with('tcp6')
  end
end

describe port(53) do
  it "listening with udp" do
    expect(subject).to be_listening.with('udp')
  end
end

describe port(53) do
  it "listening with udp6" do
    expect(subject).to be_listening.with('udp6')
  end
end
```

You can specificy local binding address for port (this features requires `gem 'serverspec', '~> 2.0.0.beta8'`).

```ruby
describe port(80) do
  it { should be_listening.on('127.0.0.1').with('tcp') }
end
```

```ruby
describe port(80) do
  it "listening on the correctly bound address with tcp" do
    expect(subject).to be_listening.on('127.0.0.1').with('tcp')
  end
end
```
