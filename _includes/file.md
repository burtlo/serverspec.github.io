### <a name="file">file</a>

File and directory resource type.

#### be_file

In order to test a subject exists as a file, you should use **be_file** matcher.

```ruby
describe file('/etc/passwd') do
  it { should be_file }
end
```

```ruby
describe file('/etc/passwd') do
  it "is a file" do
    expect(subject).to be_file
  end
end
```

#### be_directory

In order to test a subject exists as a directory, you should use **be_directory** matcher.

```ruby
describe file('/var/log/httpd') do
  it { should be_directory }
end
```

```ruby
describe file('/var/log/httpd') do
  it "is a directory" do
    expect(subject).to be_directory
  end
end
```

#### be_socket

In order to test a subject exists as a socket, you should use **be_socket** matcher.

```ruby
describe file('/var/run/unicorn.sock') do
  it { should be_socket }
end
```

```ruby
describe file('/var/run/unicorn.sock') do
  it "is a socket" do
    expect(subject).to be_socket
  end
end
```

#### contain

**Notice: Instead of ``contain``, you can use ``its(:content)`` and any standard rspec matchers. The matcher ``contain`` will be obsoleted.**

```ruby
describe file('/etc/httpd/conf/httpd.conf') do
  its(:content) { should match /ServerName www.example.jp/ }
end
```

```ruby
describe file('/etc/httpd/conf/httpd.conf') do
  it "has the correct content" do
    expect(subject.content).to match(/ServerName www.example.jp/)
  end
end
```

In order to test a file contains a given string, you can use **contain** matcher.

```ruby
describe file('/etc/httpd/conf/httpd.conf') do
  it { should contain 'ServerName www.example.jp' }
end
```

```ruby
describe file('/etc/httpd/conf/httpd.conf') do
  it "contains the correct content" do
    expect(subject).to contain('ServerName www.example.jp')
  end
end
```

You can test a file contains a given string within a given range.

```ruby
describe file('Gemfile') do
  # test 'rspec' exists between "group :test do" and "end".
  it { should contain('rspec').from(/^group :test do/).to(/^end/) }

  # test 'rspec' exists after "group :test do".
  it { should contain('rspec').after(/^group :test do/) }

  # test 'rspec' exists before "end".
  it { should contain('rspec').before(/^end/) }
end
```

```ruby
describe file('Gemfile') do
  # test 'rspec' exists between "group :test do" and "end".
  it "contains rspec in the correct location" do
    expect(subject).to contain('rspec').from(/^group :test do/).to(/^end/)
  end

  # test 'rspec' exists after "group :test do".
  it "contains rspec in the correct location" do
    expect(subject).to contain('rspec').after(/^group :test do/)
  end

  # test 'rspec' exists before "end".
  it "contains rspec in the correct location" do
    expect(subject).to contain('rspec').before(/^end/)
  end

end
```

#### be_mode

In order to test a subject is set to given mode, you should use **be_mode** matcher.

```ruby
describe file('/etc/sudoers') do
  it { should be_mode 440 }
end
```

```ruby
describe file('/etc/sudoers') do
  it "has the correct mode" do
    expect(subject).to be_mode(440)
  end
end
```

#### be\_owned\_by

In order to test a subject is owned by a given user, you should use **be\_owned\_by** matcher.

```ruby
describe file('/etc/sudoers') do
  it { should be_owned_by 'root' }
end
```

```ruby
describe file('/etc/sudoers') do
  it "has the correct owner" do
    expect(subject).to be_owned_by('root')
  end
end
```

#### be\_grouped\_into

In order to test a subject is grouped into a given group, you should use **be\_grouped\_into** matcher.

```ruby
describe file('/etc/sudoers') do
  it { should be_grouped_into 'wheel' }
end
```

```ruby
describe file('/etc/sudoers') do
  it "has the correct group" do
    expect(subject).to be_grouped_into('wheel')
  end
end
```

#### be\_linked\_to

In order to test a subject is linked to a given file or directory, you should use **be\_linked\_to** matcher.

```ruby
describe file('/etc/system-release') do
  it { should be_linked_to '/etc/redhat-release' }
end
```

```ruby
describe file('/etc/system-release') do
  it "correctly linked" do
    expect(subject).to be_linked_to('/etc/redhat-release')
  end
end
```

#### be_readable

In order to test a subject is readable, you should use **be\_readable** matcher.

```ruby
describe file('/etc/sudoers') do
  it { should be_readable }
end
```

```ruby
describe file('/etc/sudoers') do
  it "is readable" do
    expect(subject).to be_readable
  end
end
```


You can also test a subject is readable by owner, group members, others or a specific user.

```ruby
describe file('/etc/sudoers') do
  it { should be_readable.by('owner') }
  it { should be_readable.by('group') }
  it { should be_readable.by('others') }
  it { should be_readable.by_user('apache') }
end
```

```ruby
describe file('/etc/sudoers') do
  it "readable by owner" do
    expect(subject).to be_readable.by('owner')
  end

  it "readable by group" do
    expect(subject).to be_readable.by('group')
  end

  it "readable by other" do
    expect(subject).to be_readable.by('other')
  end

  it "readable by apache" do
    expect(subject).to be_readable.by_user('apache')
  end
end
```

#### be_writable

In order to test a subject is writable, you should use **be\_writable** matcher.

```ruby
describe file('/etc/sudoers') do
  it { should be_writable }
end
```

```ruby
describe file('/etc/sudoers') do
  it "is writable" do
    expect(subject).to be_writable
  end
end
```

You can also test a subject is writable by owner, group members, others or a specific user.

```ruby
describe file('/etc/sudoers') do
  it { should be_writable.by('owner') }
  it { should be_writable.by('group') }
  it { should be_writable.by('others') }
  it { should be_writable.by_user('apache') }
end
```

```ruby
describe file('/etc/sudoers') do
  it "readable by owner" do
    expect(subject).to be_writable.by('owner')
  end

  it "readable by group" do
    expect(subject).to be_writable.by('group')
  end

  it "readable by other" do
    expect(subject).to be_writable.by('other')
  end

  it "readable by apache" do
    expect(subject).to be_writable.by_user('apache')
  end
end
```


#### be_executable

In order to test a subject is executable, you should use **be\_executable** matcher.

```ruby
describe file('/etc/init.d/httpd') do
  it { should be_executable }
end
```

```ruby
describe file('/etc/init.d/httpd') do
  it "is executable" do
    expect(subject).to be_executable
  end
end
```

You can also test a subject is executable by owner, group members, others or a specific user.

```ruby
describe file('/etc/init.d/httpd') do
  it { should be_executable.by('owner') }
  it { should be_executable.by('group') }
  it { should be_executable.by('others') }
  it { should be_executable.by_user('httpd') }
end
```

```ruby
describe file('/etc/sudoers') do
  it "executable by owner" do
    expect(subject).to be_executable.by('owner')
  end

  it "executable by group" do
    expect(subject).to be_executable.by('group')
  end

  it "executable by other" do
    expect(subject).to be_executable.by('other')
  end

  it "executable by httpd" do
    expect(subject).to be_executable.by_user('httpd')
  end
end
```

#### be_mounted

In order to test a directory is mounted, you should use **be\_mounted** matcher.

```ruby
describe file('/') do
  it { should be_mounted }
end
```

```ruby
describe file('/') do
  it "is mounted" do
    expect(subject).to be_mounted
  end
end
```


You can also test a directory is mounted with correct attributes.

```ruby
describe file('/') do
  it { should be_mounted.with( :type => 'ext4' ) }
end

describe file('/') do
  it { should be_mounted.with( :options => { :rw => true } ) }
end

describe file('/') do
  it do
    should be_mounted.only_with(
      :device  => '/dev/mapper/VolGroup-lv_root',
      :type    => 'ext4',
      :options => {
        :rw   => true,
        :mode => 620,
      }
    )
  end
end
```

``only_with`` needs all attributes of the mounted directory.

```ruby
describe file('/') do
  it "mounted with ext4" do
    expect(subject).to be_mounted.with( :type => 'ext4' )
  end
end

describe file('/') do
  it "mounted with read/write true" do
    expect(subject).to be_mounted.with( :options => { :rw => true } )
  end
end

describe file('/') do
  it "mounted with the correct options" do
    expect(subject).to be_mounted.only_with(
      :device  => '/dev/mapper/VolGroup-lv_root',
      :type    => 'ext4',
      :options => {
        :rw   => true,
        :mode => 620,
      }
    )
  end
end
```

#### be_version

In order to test a file's version using its metadata in Windows, you should use **be_version** matcher.

```ruby
describe file('C:\\Windows\\System32\\wuapi.dll') do
  it { should be_version('7.6.7600.256') }
end
```

```ruby
describe file('C:\\Windows\\System32\\wuapi.dll') do
  it "correct version" do
    expect(subject).to be_version('7.6.7600.256')
  end
end
```

#### its(:md5sum)

In order to test a file's md5 checksum matches a given value, you should use **its(:md5sum)**.

```ruby
describe file('/etc/services') do
  its(:md5sum) { should eq '35435ea447c19f0ea5ef971837ab9ced' }
end
```

```ruby
describe file('/etc/services') do
  it "correct md5 sum" do
    expect(subject.md5sum).to eq('35435ea447c19f0ea5ef971837ab9ced')
  end
end
```

#### its(:sha256sum)

In order to test a file's sha256 checksum matches a given value, you should use **its(:sha256sum)**.

```ruby
describe file('/etc/services') do
  its(:sha256sum) { should eq 'a861c49e9a76d64d0a756e1c9125ae3aa6b88df3f814a51cecffd3e89cce6210' }
end
```

```ruby
describe file('/etc/services') do
  it "correct sha 256 sum" do
    expect(subject.sha256sum).to eq('a861c49e9a76d64d0a756e1c9125ae3aa6b88df3f814a51cecffd3e89cce6210')
  end
end
```
