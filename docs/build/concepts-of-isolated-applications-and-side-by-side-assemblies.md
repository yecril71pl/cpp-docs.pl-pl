---
title: Pojęcia związane z aplikacjami izolowanymi oraz aplikacjami wykonywanymi równocześnie
ms.date: 11/04/2016
helpviewer_keywords:
- side-by-side assemblies [C++]
- isolated assemblies [C++]
ms.assetid: 945a885f-cb3e-4c8a-a0b9-2c2e3e02cc50
ms.openlocfilehash: 61da61b4a213c01ca66e8978c78622fe8b2818d1
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57817585"
---
# <a name="concepts-of-isolated-applications-and-side-by-side-assemblies"></a>Pojęcia związane z aplikacjami izolowanymi oraz aplikacjami wykonywanymi równocześnie

Aplikacja jest uznawana za [izolowany aplikacji](/windows/desktop/SbsCs/isolated-applications) Jeśli wszystkie jej składniki są [zestawów side-by-side](/windows/desktop/SbsCs/about-side-by-side-assemblies-). Zestaw równoległy to zbiór zasobów — grupa bibliotek DLL, klas okien, serwerów COM, bibliotek typów lub interfejsów — które są wdrożone razem i udostępniane aplikacji do użytku w czasie wykonywania. Zwykle zestaw równoległy ma postać jednej lub kilku bibliotek DLL.

## <a name="shared-or-private"></a>Współużytkowany lub prywatny

Zestaw równoległy może być współużytkowany lub prywatny. [Współużytkowane zestawy side-by-side](https://msdn.microsoft.com/library/aa375996.aspx) mogą być używane przez wiele aplikacji, które określają w swoich manifestach zależność w zestawie. Wiele wersji zestawu równoległego może być współużytkowanych przez różne aplikacje, które są uruchomione w tym samym czasie. A [zestaw prywatny](/windows/desktop/SbsCs/about-private-assemblies-) to zestaw, który jest wdrażany wraz z aplikacją do wyłącznego użytku przez tę aplikację. Zestawy prywatne są instalowane w folderze, który zawiera plik wykonywalny aplikacji, lub w jednym z jego podfolderów.

## <a name="manifests-and-search-order"></a>Manifesty i kolejność wyszukiwania

Zarówno aplikacje izolowane, jak i zestawów side-by-side są opisane przez [manifesty](/windows/desktop/sbscs/manifests). Manifest to dokument XML, który może być plikiem zewnętrznym, może też być osadzony w aplikacji lub zestawie jako zasób. Plik manifestu aplikacji izolowanej jest używany do zarządzania nazwami i wersjami współużytkowanych zestawów równoległych, z którymi aplikacja powinna być związana w czasie wykonywania. Manifest zestawu równoległego określa nazwy, wersje, zasoby i zestawy zależne zestawów równoległych. Manifest współużytkowanego zestawu równoległego jest zainstalowany w folderze %WINDIR%\WinSxS\Manifests\. W przypadku zestawu prywatnego zaleca się włączenie jego manifestu do biblioteki DLL jako zasobu, którego identyfikator jest równy 1. Możesz również nadać zestawowi prywatnemu taką samą nazwę, jaką ma biblioteka DLL. Aby uzyskać więcej informacji, zobacz [o zestawy prywatne](/windows/desktop/SbsCs/about-private-assemblies-).

W czasie wykonywania system Windows używa informacji o zestawie z manifestu aplikacji, aby wyszukać i załadować odpowiedni zestaw równoległy. Jeśli aplikacja izolowana określa zależność od zestawu, system operacyjny najpierw szuka zestawu wśród zestawów współużytkowanych w pamięci podręcznej macierzystego zestawu w folderze %WINNDIR%\WinSxS\. Jeśli wymagany zestaw nie zostanie znaleziony, system operacyjny wyszukuje zestaw prywatny w folderze struktury katalogów aplikacji. Aby uzyskać więcej informacji, zobacz [kolejność wyszukiwania zestawu](/windows/desktop/SbsCs/assembly-searching-sequence).

## <a name="changing-dependencies"></a>Zmiana zależności

Możesz zmienić zależności zestawów side-by-side, po wdrożeniu aplikacji, modyfikując [pliki konfiguracyjne wydawcy](/windows/desktop/SbsCs/publisher-configuration-files) i [pliki konfiguracyjne aplikacji](/windows/desktop/SbsCs/application-configuration-files). Plik konfiguracyjny wydawcy, znany również jako plik zasad wydawcy, to plik XML, który globalnie przekierowuje aplikacje i zestawy z korzystania z jednej wersji zestawu równoległego do korzystania z innej wersji tego samego zestawu. Na przykład, możesz zmienić zależność, gdy w zestawie równoległym zostanie naprawiony błąd lub wprowadzona poprawka bezpieczeństwa i chcesz przekierować wszystkie aplikacje tak, aby używały poprawionej wersji. Plik konfiguracyjny aplikacji to plik XML, który przekierowuje określoną aplikację z korzystania z jednej wersji zestawu równoległego do korzystania z innej wersji tego samego zestawu. Pliku konfiguracyjnego aplikacji można użyć do przekierowania określonej aplikacji tak, aby korzystała z wersji zestawu równoległego innej niż ta, która jest zdefiniowana w pliku konfiguracyjnym wydawcy. Aby uzyskać więcej informacji, zobacz [konfiguracji](/windows/desktop/SbsCs/configuration).

## <a name="visual-c-libraries"></a>Biblioteki Visual C++

W programie Visual Studio 2005 i Visual Studio 2008 redystrybucyjne biblioteki, takie jak biblioteki ATL, MFC, CRT, Standard C++, OpenMP i MSDIA zostały wcześniej wdrożone jako współużytkowane zestawy równoległe w pamięci podręcznej zestawu macierzystego. W bieżącej wersji, redystrybucyjne biblioteki używają centralnego wdrożenia. Domyślnie wszystkie aplikacje, które są tworzone przy użyciu języka Visual C++, są kompilowane z manifestem osadzonym w końcowym pliku binarnym, a manifest zawiera opis zależności pliku binarnego od bibliotek Visual C++. Informacje o tworzeniu manifestu dla aplikacji Visual C++ znajdziesz [ogólne informacje o tworzeniu manifestu dla programów C/C++](understanding-manifest-generation-for-c-cpp-programs.md). Manifest nie jest wymagany w przypadku aplikacji, które są statycznie łączone z używanymi bibliotekami, lub które używają lokalnego wdrożenia. Aby uzyskać więcej informacji na temat wdrażania, zobacz [wdrożenia w programie Visual C++](../ide/deployment-in-visual-cpp.md).

## <a name="see-also"></a>Zobacz także

[Kompilowanie aplikacji izolowanych C/C++ oraz aplikacji wykonywanych równocześnie](building-c-cpp-isolated-applications-and-side-by-side-assemblies.md)
