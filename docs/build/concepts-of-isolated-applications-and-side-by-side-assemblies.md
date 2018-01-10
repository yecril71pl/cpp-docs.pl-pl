---
title: Aplikacje izolowane i zestawy Side-by-side | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- side-by-side assemblies [C++]
- isolated assemblies [C++]
ms.assetid: 945a885f-cb3e-4c8a-a0b9-2c2e3e02cc50
caps.latest.revision: "21"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 9166f62c51344cc9c620da34d9c6fcee4665f400
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="concepts-of-isolated-applications-and-side-by-side-assemblies"></a>Pojęcia związane z aplikacjami izolowanymi oraz aplikacjami wykonywanymi równocześnie
Aplikacja jest uznawany za [izolowany aplikacji](http://msdn.microsoft.com/library/aa375190) , gdy wszystkie jego składniki są [zestawy side-by-side](http://msdn.microsoft.com/library/ff951640). Zestaw równoległy to zbiór zasobów — grupa bibliotek DLL, klas okien, serwerów COM, bibliotek typów lub interfejsów — które są wdrożone razem i udostępniane aplikacji do użytku w czasie wykonywania. Zwykle zestaw równoległy ma postać jednej lub kilku bibliotek DLL.  
  
## <a name="shared-or-private"></a>Współużytkowany lub prywatny  
 Zestaw równoległy może być współużytkowany lub prywatny. [Współużytkowane zestawy side-by-side](https://msdn.microsoft.com/en-us/library/aa375996.aspx) mogą być używane przez wiele aplikacji, które określają, w ich manifestów zależność w zestawie. Wiele wersji zestawu równoległego może być współużytkowanych przez różne aplikacje, które są uruchomione w tym samym czasie. A [zestaw prywatny](http://msdn.microsoft.com/library/ff951638) jest zestawu, który jest wdrażany razem z aplikacją do wyłącznego użytku tej aplikacji. Zestawy prywatne są instalowane w folderze, który zawiera plik wykonywalny aplikacji, lub w jednym z jego podfolderów.  
  
## <a name="manifests-and-search-order"></a>Manifesty i kolejność wyszukiwania  
 Zarówno aplikacje izolowane i zestawy side-by-side opisanym przez [manifesty](http://msdn.microsoft.com/library/aa375365). Manifest to dokument XML, który może być plikiem zewnętrznym, może też być osadzony w aplikacji lub zestawie jako zasób. Plik manifestu aplikacji izolowanej jest używany do zarządzania nazwami i wersjami współużytkowanych zestawów równoległych, z którymi aplikacja powinna być związana w czasie wykonywania. Manifest zestawu równoległego określa nazwy, wersje, zasoby i zestawy zależne zestawów równoległych. Manifest współużytkowanego zestawu równoległego jest zainstalowany w folderze %WINDIR%\WinSxS\Manifests\. W przypadku zestawu prywatnego zaleca się włączenie jego manifestu do biblioteki DLL jako zasobu, którego identyfikator jest równy 1. Możesz również nadać zestawowi prywatnemu taką samą nazwę, jaką ma biblioteka DLL. Aby uzyskać więcej informacji, zobacz [o zestawy prywatne](http://msdn.microsoft.com/library/ff951638).  
  
 W czasie wykonywania system Windows używa informacji o zestawie z manifestu aplikacji, aby wyszukać i załadować odpowiedni zestaw równoległy. Jeśli aplikacja izolowana określa zależność od zestawu, system operacyjny najpierw szuka zestawu wśród zestawów współużytkowanych w pamięci podręcznej macierzystego zestawu w folderze %WINNDIR%\WinSxS\. Jeśli wymagany zestaw nie zostanie znaleziony, system operacyjny wyszukuje zestaw prywatny w folderze struktury katalogów aplikacji. Aby uzyskać więcej informacji, zobacz [sekwencji wyszukiwania zestawu](http://msdn.microsoft.com/library/aa374224).  
  
## <a name="changing-dependencies"></a>Zmiana zależności  
 Zależności zestawu side-by-side można zmienić po wdrożeniu aplikacji, modyfikując [pliki konfiguracji wydawcy](http://msdn.microsoft.com/library/aa375682) i [pliki konfiguracji aplikacji](http://msdn.microsoft.com/library/aa374182). Plik konfiguracyjny wydawcy, znany również jako plik zasad wydawcy, to plik XML, który globalnie przekierowuje aplikacje i zestawy z korzystania z jednej wersji zestawu równoległego do korzystania z innej wersji tego samego zestawu. Na przykład, możesz zmienić zależność, gdy w zestawie równoległym zostanie naprawiony błąd lub wprowadzona poprawka bezpieczeństwa i chcesz przekierować wszystkie aplikacje tak, aby używały poprawionej wersji. Plik konfiguracyjny aplikacji to plik XML, który przekierowuje określoną aplikację z korzystania z jednej wersji zestawu równoległego do korzystania z innej wersji tego samego zestawu. Pliku konfiguracyjnego aplikacji można użyć do przekierowania określonej aplikacji tak, aby korzystała z wersji zestawu równoległego innej niż ta, która jest zdefiniowana w pliku konfiguracyjnym wydawcy. Aby uzyskać więcej informacji, zobacz [konfiguracji](http://msdn.microsoft.com/library/aa375123).  
  
## <a name="visual-c-libraries"></a>Biblioteki Visual C++  
 W programie Visual Studio 2005 i Visual Studio 2008 redystrybucyjne biblioteki, takie jak biblioteki ATL, MFC, CRT, Standard C++, OpenMP i MSDIA zostały wcześniej wdrożone jako współużytkowane zestawy równoległe w pamięci podręcznej zestawu macierzystego. W bieżącej wersji, redystrybucyjne biblioteki używają centralnego wdrożenia. Domyślnie wszystkie aplikacje, które są tworzone przy użyciu języka Visual C++, są kompilowane z manifestem osadzonym w końcowym pliku binarnym, a manifest zawiera opis zależności pliku binarnego od bibliotek Visual C++. Aby dowiedzieć się o tworzeniu manifestu dla aplikacji Visual C++, zobacz [opis Generowanie manifestu dla programów C/C++](../build/understanding-manifest-generation-for-c-cpp-programs.md). Manifest nie jest wymagany w przypadku aplikacji, które są statycznie łączone z używanymi bibliotekami, lub które używają lokalnego wdrożenia. Aby uzyskać więcej informacji na temat wdrażania, zobacz [wdrożenia w programie Visual C++](../ide/deployment-in-visual-cpp.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Kompilowanie aplikacji izolowanych C/C++ oraz aplikacji wykonywanych równocześnie](../build/building-c-cpp-isolated-applications-and-side-by-side-assemblies.md)