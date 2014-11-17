### <a name="user">user</a>

User resource type.

#### exist

In order to test a subject exists as a user, you should use **exist** matcher.

```ruby
describe user('root') do
  it { should exist }
end
```

```ruby
describe user('root') do
  it "exists" do
    expect(subject).to exist
  end
end
```

#### belong\_to\_group

In order to test a user belongs to a given group, you should use **belong\_to\_group** matcher.

```ruby
describe user('apache') do
  it { should belong_to_group 'apache' }
end
```

```ruby
describe user('apache') do
  it "belongs to the correct group" do
    expect(subject).to belong_to_group('apache')
  end
end
```

#### have_uid

In order to test a user have a given uid, you should use **have_uid** matcher.

```ruby
describe user('root') do
  it { should have_uid 0 }
end
```

```ruby
describe user('root') do
  it "correct uid" do
    expect(subject).to have_uid(0)
  end
end
```

#### have\_home\_directory

In order to test a user have a given home directory, you should use **have\_home\_directory** matcher.

```ruby
describe user('root') do
  it { should have_home_directory '/root' }
end
```

```ruby
describe user('root') do
  it "correct home" do
    expect(subject).to have_home_directory('/root')
  end
end
```

#### have\_login\_shell

In order to test a user have a given login shell, you should use **have\_login\_shell** matcher.

```ruby
describe user('root') do
  it { should have_login_shell '/bin/bash' }
end
```

```ruby
describe user('root') do
  it "correct shell" do
    expect(subject).to have_login_shell('/bin/bash')
  end
end
```

#### have\_authorized\_key

In order to test a have have a given authorized key, you should use **have\_authorized\_key** matcher.

```ruby
describe user('root') do
  it { should have_authorized_key 'ssh-rsa ABCDEFGHIJKLMNOPQRSTUVWXYZABCDEFGHIJKLMNOPQRSTUVWXYZABCDEFGHIJKLMNOPQRSTUVWXYZABCDEFGHIJKLMNOPQRSTUVWXYZABCDEFGHIJKLMNOPQRSTUVWXYZABCDEFGHIJKLMNOPQRSTUVWXYZABCDEFGHIJKLMNOPQRSTUVWXYZABCDEFGHIJKLMNOPQRSTUVWXYZABCDEFGHIJKLMNOPQRSTUVWXYZABCDEFGHIJKLMNOPQRSTUVWXYZABCDEFGHIJKLMNOPQRSTUVWXYZABCDEFGHIJKLMNOPQRSTUVWXYZABCDEFGHIJKLMNOPQRSTUVWXYZABCDEFGHIJKLMNOPQRSTUVWXYZABCDEFGH foo@bar.local' }
end
```

```ruby
describe user('root') do
  it "correct authorized key" do
    expect(subject).to have_authorized_key('ssh-rsa ABCDEFGHIJKLMNOPQRSTUVWXYZABCDEFGHIJKLMNOPQRSTUVWXYZABCDEFGHIJKLMNOPQRSTUVWXYZABCDEFGHIJKLMNOPQRSTUVWXYZABCDEFGHIJKLMNOPQRSTUVWXYZABCDEFGHIJKLMNOPQRSTUVWXYZABCDEFGHIJKLMNOPQRSTUVWXYZABCDEFGHIJKLMNOPQRSTUVWXYZABCDEFGHIJKLMNOPQRSTUVWXYZABCDEFGHIJKLMNOPQRSTUVWXYZABCDEFGHIJKLMNOPQRSTUVWXYZABCDEFGHIJKLMNOPQRSTUVWXYZABCDEFGHIJKLMNOPQRSTUVWXYZABCDEFGHIJKLMNOPQRSTUVWXYZABCDEFGH foo@bar.local')
  end
end
```

