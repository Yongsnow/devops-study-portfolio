
Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/focal64"

  # --- Build Stage ---
  config.vm.provision "build", type: "shell", inline: <<-SHELL
    echo "Starting Build Process..."
    cd /vagrant
    mvn clean install -DskipTests
    echo "Build completed successfully" > /vagrant/local-ci-build.txt
  SHELL

  # --- Unit Test Stage ---
  config.vm.provision "test", type: "shell", inline: <<-SHELL
    echo "Running Unit Tests..."
    cd /vagrant
    mvn test
    echo "Unit tests completed successfully" > /vagrant/local-ci-test.txt
  SHELL
end