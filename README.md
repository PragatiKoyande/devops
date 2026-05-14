@echo off

set ENV=%1

if "%ENV%"=="" (
    echo Please provide environment
    echo Example:
    echo deploy-all.bat uat
    exit /b 1
)

set NAMESPACE=backend-%ENV%

echo Deploying all microservices to %ENV% environment...

cd common-master
helm upgrade --install common-master . -f values-%ENV%.yaml -n %NAMESPACE% --create-namespace
cd ..

cd common-request
helm upgrade --install common-request . -f values-%ENV%.yaml -n %NAMESPACE%
cd ..

cd dashboard
helm upgrade --install dashboard . -f values-%ENV%.yaml -n %NAMESPACE%
cd ..

cd enqiry-service
helm upgrade --install enqiry-service . -f values-%ENV%.yaml -n %NAMESPACE%
cd ..

cd journal
helm upgrade --install journal . -f values-%ENV%.yaml -n %NAMESPACE%
cd ..

cd login
helm upgrade --install login . -f values-%ENV%.yaml -n %NAMESPACE%
cd ..

cd notification
helm upgrade --install notification . -f values-%ENV%.yaml -n %NAMESPACE%
cd ..

cd nwsa-service
helm upgrade --install nwsa-service . -f values-%ENV%.yaml -n %NAMESPACE%
cd ..

cd process-status
helm upgrade --install process-status . -f values-%ENV%.yaml -n %NAMESPACE%
cd ..

cd react-service
helm upgrade --install react-service . -f values-%ENV%.yaml -n %NAMESPACE%
cd ..

cd redis-service
helm upgrade --install redis-service . -f values-%ENV%.yaml -n %NAMESPACE%
cd ..

cd report-builder
helm upgrade --install report-builder . -f values-%ENV%.yaml -n %NAMESPACE%
cd ..

cd report-service
helm upgrade --install report-service . -f values-%ENV%.yaml -n %NAMESPACE%
cd ..

cd template-config
helm upgrade --install template-config . -f values-%ENV%.yaml -n %NAMESPACE%
cd ..

cd transactions
helm upgrade --install transactions . -f values-%ENV%.yaml -n %NAMESPACE%
cd ..

cd user-service
helm upgrade --install user-service . -f values-%ENV%.yaml -n %NAMESPACE%
cd ..

echo.
echo All microservices deployed successfully to %ENV%