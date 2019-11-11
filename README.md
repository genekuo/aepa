# aepa
brew tap pivotal/tap && \
brew cask install java && \
brew install jq && \
brew install springboot

spring init \
--boot-version=2.1.0.RC1 \
--build=gradle \
--java-version=1.8 \
--packaging=jar \
--name=product \
--package-name=com.genekuo.microservices.product \
--groupId=com.genekuo.microservices.product \
--dependencies=actuator,webflux \
--version=1.0.0-SNAPSHOT \
product

spring init \
--boot-version=2.1.0.RC1 \
--build=gradle \
--java-version=1.8 \
--packaging=jar \
--name=orders \
--package-name=com.genekuo.microservices.orders \
--groupId=com.genekuo.microservices.orders \
--dependencies=actuator,webflux \
--version=1.0.0-SNAPSHOT \
orders

find product -type f

cp -r product/gradle .
cp product/gradlew .
cp product/gradlew.bat .
cp product/.gitignore .

find product -depth -name "gradle" -exec rm -rfv "{}" \;
find product -depth -name "gradlew*" -exec rm -rfv "{}" \;
find orders -depth -name "gradle" -exec rm -rfv "{}" \;
find orders -depth -name "gradlew*" -exec rm -rfv "{}" \;
