@ECHO off
SET interactive=0
COLOR 1E

:: LidlCommander tool for Spanish Team 
:: Wincor-Nixdorf Poland 2016
:: Creative Commons - Jaime Villar Camacho
:: No kasierka were harmed during execution of this script
:: Beta 0.0.1

:: function pinging (sub-options)
:start
cls
ECHO.
ECHO ++====[ Bienvenido a LidlPinger ]====++
ECHO +++ Por favor seleccione una opcion +++
ECHO.
ECHO Por favor seleccione una opcion
ECHO.
ECHO 1) Telefonica
ECHO 2) VPN
ECHO 3) Caja
ECHO 4) Back Office
ECHO 5) Impresora
ECHO 0) Salir
ECHO.
ECHO ++====================================++
ECHO.

	:: options
	SET /P var=Escriba el numero de la opcion [1-5] o salir:
	IF "%var%"=="1"  GOTO telefonica
	IF "%var%"=="2"  GOTO vpn
	IF "%var%"=="3"  GOTO caja
	IF "%var%"=="4"  GOTO bo
	IF "%var%"=="5"	 GOTO impresora
	IF "%var%"=="0"  GOTO salir
	ECHO.

	:: exception when out of option range
	ECHO El numero %var% no es una opcion valida, intentelo de nuevo.
	ECHO.
	PAUSE
	ECHO.
	GOTO start

	
	:telefonica
	ECHO.
	ECHO + (1) Ping Telefonica +
	ECHO.
	SET /P store=Escriba el numero de tienda con 4 digitos:
	ECHO.
	SET /P n=Escriba el numero de repeticiones del ping:
	ECHO.
	
	ping es-%store%nr01 -n "%n%"
	
	PAUSE
	GOTO start
	
	:: exception when out of option range
	ECHO.
	ECHO El numero de tienda %store% no es correcto, intentelo de nuevo.
	ECHO.
	PAUSE
	ECHO.
	GOTO telefonica	


	:vpn
	ECHO.
	ECHO + (2) Ping VPN +
	ECHO.
	SET /P store=Escriba el numero de tienda con 4 digitos:
	ECHO.
	SET /P n=Escriba el numero de repeticiones del ping:
	ECHO.
	
	ping es-"%store%"vpn01 -n "%n%"

	PAUSE
	GOTO start
	
	:: exception when out of option range
	ECHO.
	ECHO El numero de tienda %store% no es correcto, intentelo de nuevo.
	ECHO.
	PAUSE
	ECHO.
	GOTO vpn


	:caja
	ECHO.
	ECHO + (3) Ping Caja +
	ECHO.
	SET /P store=Escriba el numero de tienda con 4 digitos:
	SET /P till=Escriba el numero de la caja con 2 digitos:
	ECHO.
	SET /P n=Escriba el numero de repeticiones del ping:
	ECHO.
	
	ping es-"%store%"TI"%till%" -n "%n%"
	
	PAUSE
	GOTO start
	
	:: exception when out of option range
	ECHO.
	ECHO El numero de tienda o caja no es correcto, intentelo de nuevo..
	ECHO.
	PAUSE
	ECHO.
	GOTO caja	


	:bo
	ECHO.
	ECHO + (4) Ping Back Office +
	ECHO.
	SET /P store=Escriba el numero de tienda con 4 digitos:
	ECHO.
	SET /P n=Escriba el numero de repeticiones del ping:
	ECHO.
	
	ping es-"%store%"bo01 -n "%n%"
	
	PAUSE
	GOTO start
	
	:: exception when out of option range
	ECHO.
	ECHO El numero de tienda %store% no es correcto, intentelo de nuevo.
	ECHO.
	PAUSE
	ECHO.
	GOTO bo

	PAUSE
	ECHO.
	GOTO start
	
	
	:impresora
	ECHO.
	ECHO + (5) Ping Impresora +
	ECHO.
	SET /P store=Escriba el numero de tienda con 4 digitos:
	ECHO.
	SET /P n=Escriba el numero de repeticiones del ping:
	ECHO.
	
	ping es-%store%np01 -n "%n%"
	
	PAUSE
	GOTO start

	:: exception when out of option range
	ECHO.
	ECHO El numero de tienda %store% no es correcto, intentelo de nuevo.
	ECHO.
	PAUSE
	ECHO.
	GOTO impresora	

:: exit 
@cls&exit

:: EoF
ENDLOCAL
ECHO ON
@EXIT /B 0	
