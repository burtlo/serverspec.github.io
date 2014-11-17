### <a name="service">service</a>

Service resource type.

#### be_enabled

In order to test a given service is enabled(automatically start when OS booting up), you should use **be_enabled** matcher.

```ruby
describe service('ntpd') do
  it { should be_enabled }
end
```

```ruby
describe service('ntpd') do
  it "enabled" do
    expect(subject).to be_enabled
  end
end
```

You can test a service is enabled with a given run level.(This works only with Red Hat and Debian family currently.)

```ruby
describe service('ntpd') do
  it { should be_enabled.with_level(3) }
end
```

```ruby
describe service('ntpd') do
  it "enabled with level 3" do
    expect(subject).to be_enabled.with_level(3)
  end
end
```

#### be_installed

In order to test a given service is installed, you should use **be_installed** matcher.

*Currently only supported in Windows*

```ruby
describe service('DNS Client') do
  it { should be_installed }
end
```

```ruby
describe service('DNS Client') do
  it "installed" do
    expect(subject).to be_installed
  end
end
```

#### be_running

In order to test a given service/process is running, you should use **be_running** matcher.

```ruby
describe service('ntpd') do
  it { should be_running }
end
```

```ruby
describe service('ntpd') do
  it "is running" do
    expect(subject).to be_running
  end
end
```

You can test a given service/process is running under [supervisor](http://supervisord.org/).

```ruby
describe service('ntpd') do
  it { should be_running.under('supervisor') }
end
```

```ruby
describe service('ntpd') do
  it "running under supervisor" do
    expect(subject).to be_running.under('supervisor')
  end
end
```

#### be\_monitored\_by

In order to test a service/process is monitored by a given software, you should use **be\_monitored\_by** matcher.

```ruby
describe service('sshd') do
  it { should be_monitored_by('monit') }
end

describe service('unicorn') do
  it { should be_monitored_by('god') }
end
```

```ruby
describe service('sshd') do
  it "monitored by monit" do
    expect(subject).to be_monitored_by('monit')
  end
end

describe service('unicorn') do
  it "monitored by god" do
    expect(subject).to be_monitored_by('god')
  end
end
```


#### have\_start\_mode

In order to test a service's startup mode is correct, you should use **have\_start\_mode** matcher.

*Currently only supported in Windows*

```ruby
describe service('DNS Client') do
  it { should have_start_mode('Manual') }
end
```

```ruby
describe service('DNS Client') do
  it "has a manual start mode" do
    expect(subject).to have_start_mode('Manual')
  end
end
```
