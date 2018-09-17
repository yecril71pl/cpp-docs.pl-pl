---
title: Pojęcia związane z aplikacjami izolowanymi oraz aplikacjami zestawów Side-by-side | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- side-by-side assemblies [C++]
- isolated assemblies [C++]
ms.assetid: 945a885f-cb3e-4c8a-a0b9-2c2e3e02cc50
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 27ecefc5e448a1040e7eff3e45b94b0a31fbfc87
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45710259"
---
# <a name="concepts-of-isolated-applications-and-side-by-side-assemblies"></a>Pojęcia związane z aplikacjami izolowanymi oraz aplikacjami wykonywanymi równocześnie

Aplikacja jest uznawana za [izolowany aplikacji](/windows/desktop/SbsCs/isolated-applications) Jeśli wszystkie jej składniki są [zestawów side-by-side](/windows/desktop/SbsCs/about-side-by-side-assemblies-). Zestaw równoległy to zbiór zasobów — grupa bibliotek DLL, klas okien, serwerów COM, bibliotek typów lub interfejsów — które są wdrożone razem i udostępniane aplikacji do użytku w czasie wykonywania. Zwykle zestaw równoległy ma postać jednej lub kilku bibliotek DLL.

## <a name="shared-or-private"></a>Współużytkowany lub prywatny

Zestaw równoległy może być współużytkowany lub prywatny. [Współużytkowane zestawy side-by-side](https://msdn.microsoft.com/library/aa375996.aspx) mogą być używane przez wiele aplikacji, które określają w swoich manifestach zależność w zestawie. Wiele wersji zestawu równoległego może być współużytkowanych przez różne aplikacje, które są uruchomione w tym samym czasie. A [zestaw prywatny](/windows/desktop/SbsCs/about-private-assemblies-) to zestaw, który jest wdrażany wraz z aplikacją do wyłącznego użytku przez tę aplikację. Zestawy prywatne są instalowane w folderze, który zawiera plik wykonywalny aplikacji, lub w jednym z jego podfolderów.

## <a name="manifests-and-search-order"></a>Manifesty i kolejność wyszukiwania

Zarówno aplikacje izolowane, jak i zestawów side-by-side są opisane przez [manifesty](https://msdn.microsoft.com/library/aa375365). Manifest to dokument XML, który może być plikiem zewnętrznym, może też być osadzony w aplikacji lub zestawie jako zasób. Plik manifestu aplikacji izolowanej jest używany do zarządzania nazwami i wersjami współużytkowanych zestawów równoległych, z którymi aplikacja powinna być związana w czasie wykonywania. Manifest zestawu równoległego określa nazwy, wersje, zasoby i zestawy zależne zestawów równoległych. Manifest współużytkowanego zestawu równoległego jest zainstalowany w folderze %WINDIR%\WinSxS\Manifests\. W przypadku zestawu prywatnego zaleca się włączenie jego manifestu do biblioteki DLL jako zasobu, którego identyfikator jest równy 1. Możesz również nadać zestawowi prywatnemu taką samą nazwę, jaką ma biblioteka DLL. Aby uzyskać więcej informacji, zobacz [o zestawy prywatne](/windows/desktop/SbsCs/about-private-assemblies-).

W czasie wykonywania system Windows używa informacji o zestawie z manifestu aplikacji, aby wyszukać i załadować odpowiedni zestaw równoległy. Jeśli aplikacja izolowana określa zależność od zestawu, system operacyjny najpierw szuka zestawu wśród zestawów współużytkowanych w pamięci podręcznej macierzystego zestawu w folderze %WINNDIR%\WinSxS\. Jeśli wymagany zestaw nie zostanie znaleziony, system operacyjny wyszukuje zestaw prywatny w folderze struktury katalogów aplikacji. Aby uzyskać więcej informacji, zobacz [kolejność wyszukiwania zestawu](/windows/desktop/SbsCs/assembly-searching-sequence).

## <a name="changing-dependencies"></a>Zmiana zależności

Możesz zmienić zależności zestawów side-by-side, po wdrożeniu aplikacji, modyfikując [pliki konfiguracyjne wydawcy](/windows/desktop/SbsCs/publisher-configuration-files) i [pliki konfiguracyjne aplikacji](/windows/desktop/SbsCs/application-configuration-files). Plik konfiguracyjny wydawcy, znany również jako plik zasad wydawcy, to plik XML, który globalnie przekierowuje aplikacje i zestawy z korzystania z jednej wersji zestawu równoległego do korzystania z innej wersji tego samego zestawu. Na przykład, możesz zmienić zależność, gdy w zestawie równoległym zostanie naprawiony błąd lub wprowadzona poprawka bezpieczeństwa i chcesz przekierować wszystkie aplikacje tak, aby używały poprawionej wersji. Plik konfiguracyjny aplikacji to plik XML, który przekierowuje określoną aplikację z korzystania z jednej wersji zestawu równoległego do korzystania z innej wersji tego samego zestawu. Pliku konfiguracyjnego aplikacji można użyć do przekierowania określonej aplikacji tak, aby korzystała z wersji zestawu równoległego innej niż ta, która jest zdefiniowana w pliku konfiguracyjnym wydawcy. Aby uzyskać więcej informacji, zobacz [konfiguracji](/windows/desktop/SbsCs/configuration).

## <a name="visual-c-libraries"></a>Biblioteki Visual C++

W programie Visual Studio 2005 i Visual Studio 2008 redystrybucyjne biblioteki, takie jak biblioteki ATL, MFC, CRT, Standard C++, OpenMP i MSDIA zostały wcześniej wdrożone jako współużytkowane zestawy równoległe w pamięci podręcznej zestawu macierzystego. W bieżącej wersji, redystrybucyjne biblioteki używają centralnego wdrożenia. Domyślnie wszystkie aplikacje, które są tworzone przy użyciu języka Visual C++, są kompilowane z manifestem osadzonym w końcowym pliku binarnym, a manifest zawiera opis zależności pliku binarnego od bibliotek Visual C++. Informacje o tworzeniu manifestu dla aplikacji Visual C++ znajdziesz [ogólne informacje o tworzeniu manifestu dla programów C/C++](../build/understanding-manifest-generation-for-c-cpp-programs.md). Manifest nie jest wymagany w przypadku aplikacji, które są statycznie łączone z używanymi bibliotekami, lub które używają lokalnego wdrożenia. Aby uzyskać więcej informacji na temat wdrażania, zobacz [wdrożenia w programie Visual C++](../ide/deployment-in-visual-cpp.md).

## <a name="see-also"></a>Zobacz też

[Kompilowanie aplikacji izolowanych C/C++ oraz aplikacji wykonywanych równocześnie](../build/building-c-cpp-isolated-applications-and-side-by-side-assemblies.md)