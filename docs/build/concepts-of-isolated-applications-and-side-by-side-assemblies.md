---
title: Pojęcia związane z aplikacjami izolowanymi oraz aplikacjami wykonywanymi równocześnie
ms.date: 05/06/2019
helpviewer_keywords:
- side-by-side assemblies [C++]
- isolated assemblies [C++]
ms.assetid: 945a885f-cb3e-4c8a-a0b9-2c2e3e02cc50
ms.openlocfilehash: f75a95ccca214f437152d13e099fbd9d03eaaee2
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69493308"
---
# <a name="concepts-of-isolated-applications-and-side-by-side-assemblies"></a>Pojęcia związane z aplikacjami izolowanymi oraz aplikacjami wykonywanymi równocześnie

Aplikacja jest traktowana jako [aplikacja izolowana](/windows/win32/SbsCs/isolated-applications) , jeśli wszystkie jej składniki są [zestawami równoległymi](/windows/win32/SbsCs/about-side-by-side-assemblies-). Zestaw równoległy to zbiór zasobów — grupa bibliotek DLL, klas okien, serwerów COM, bibliotek typów lub interfejsów — które są wdrożone razem i udostępniane aplikacji do użytku w czasie wykonywania. Zwykle zestaw równoległy ma postać jednej lub kilku bibliotek DLL.

## <a name="shared-or-private"></a>Współużytkowany lub prywatny

Zestaw równoległy może być współużytkowany lub prywatny. [Współużytkowane zestawy równoległe](/windows/win32/sbscs/about-shared-assemblies-) mogą być używane przez wiele aplikacji, które określają, w ich manifestach, zależność od zestawu. Wiele wersji zestawu równoległego może być współużytkowanych przez różne aplikacje, które są uruchomione w tym samym czasie. [Zestaw prywatny](/windows/win32/SbsCs/about-private-assemblies-) to zestaw, który jest wdrażany wraz z aplikacją do wyłącznego użycia tej aplikacji. Zestawy prywatne są instalowane w folderze, który zawiera plik wykonywalny aplikacji, lub w jednym z jego podfolderów.

## <a name="manifests-and-search-order"></a>Manifesty i kolejność wyszukiwania

Zarówno aplikacje izolowane, jak i zestawy równoległe są opisane przez [manifesty](/windows/win32/sbscs/manifests). Manifest to dokument XML, który może być plikiem zewnętrznym, może też być osadzony w aplikacji lub zestawie jako zasób. Plik manifestu aplikacji izolowanej jest używany do zarządzania nazwami i wersjami współużytkowanych zestawów równoległych, z którymi aplikacja powinna być związana w czasie wykonywania. Manifest zestawu równoległego określa nazwy, wersje, zasoby i zestawy zależne zestawów równoległych. Manifest współużytkowanego zestawu równoległego jest zainstalowany w folderze %WINDIR%\WinSxS\Manifests\. W przypadku zestawu prywatnego zaleca się włączenie jego manifestu do biblioteki DLL jako zasobu, którego identyfikator jest równy 1. Możesz również nadać zestawowi prywatnemu taką samą nazwę, jaką ma biblioteka DLL. Aby uzyskać więcej informacji, zobacz [Informacje o prywatnych zestawach](/windows/win32/SbsCs/about-private-assemblies-).

W czasie wykonywania system Windows używa informacji o zestawie z manifestu aplikacji, aby wyszukać i załadować odpowiedni zestaw równoległy. Jeśli aplikacja izolowana określa zależność od zestawu, system operacyjny najpierw szuka zestawu wśród zestawów współużytkowanych w pamięci podręcznej macierzystego zestawu w folderze %WINNDIR%\WinSxS\. Jeśli wymagany zestaw nie zostanie znaleziony, system operacyjny wyszukuje zestaw prywatny w folderze struktury katalogów aplikacji. Aby uzyskać więcej informacji, zobacz [sekwencja wyszukiwania zestawów](/windows/win32/SbsCs/assembly-searching-sequence).

## <a name="changing-dependencies"></a>Zmiana zależności

Zależności zestawów równoległych można zmienić po wdrożeniu aplikacji, modyfikując [pliki konfiguracji wydawcy](/windows/win32/SbsCs/publisher-configuration-files) i [pliki konfiguracji aplikacji](/windows/win32/SbsCs/application-configuration-files). Plik konfiguracyjny wydawcy, znany również jako plik zasad wydawcy, to plik XML, który globalnie przekierowuje aplikacje i zestawy z korzystania z jednej wersji zestawu równoległego do korzystania z innej wersji tego samego zestawu. Na przykład, możesz zmienić zależność, gdy w zestawie równoległym zostanie naprawiony błąd lub wprowadzona poprawka bezpieczeństwa i chcesz przekierować wszystkie aplikacje tak, aby używały poprawionej wersji. Plik konfiguracyjny aplikacji to plik XML, który przekierowuje określoną aplikację z korzystania z jednej wersji zestawu równoległego do korzystania z innej wersji tego samego zestawu. Pliku konfiguracyjnego aplikacji można użyć do przekierowania określonej aplikacji tak, aby korzystała z wersji zestawu równoległego innej niż ta, która jest zdefiniowana w pliku konfiguracyjnym wydawcy. Aby uzyskać więcej informacji, zobacz [konfiguracji](/windows/win32/SbsCs/configuration).

## <a name="visual-c-libraries"></a>Biblioteki Visual C++

W programie Visual Studio 2005 i Visual Studio 2008 redystrybucyjne biblioteki, takie jak biblioteki ATL, MFC, CRT, Standard C++, OpenMP i MSDIA zostały wcześniej wdrożone jako współużytkowane zestawy równoległe w pamięci podręcznej zestawu macierzystego. W bieżącej wersji, redystrybucyjne biblioteki używają centralnego wdrożenia. Domyślnie wszystkie aplikacje skompilowane przy użyciu programu Visual Studio są kompilowane z manifestem osadzonym w końcowym pliku binarnym, a manifest opisuje zależności pliku binarnego w bibliotekach wizualizacji C++ . Aby zrozumieć generowanie manifestu dla C++ aplikacji, zobacz [Opis generowania manifestu dla języka CC++ /programów](understanding-manifest-generation-for-c-cpp-programs.md). Manifest nie jest wymagany w przypadku aplikacji, które są statycznie łączone z używanymi bibliotekami, lub które używają lokalnego wdrożenia. Aby uzyskać więcej informacji o wdrażaniu, zobacz [wdrażanie C++w programie Visual ](../windows/deployment-in-visual-cpp.md).

## <a name="see-also"></a>Zobacz także

[Kompilowanie aplikacji izolowanych C/C++ oraz aplikacji wykonywanych równocześnie](building-c-cpp-isolated-applications-and-side-by-side-assemblies.md)
