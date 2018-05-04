---
title: Kompilowanie zestawów C/C++ Side-by-side | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- side-by-side applications [C++]
ms.assetid: 7fa20b16-3737-4f76-a0b5-1dacea19a1e8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a45062af5648c7b3565d959fd1d2dce13aeca4b3
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="building-cc-side-by-side-assemblies"></a>Kompilowanie wykonywanych jednocześnie aplikacji C/C++
A [zestawu side-by-side](http://msdn.microsoft.com/library/windows/desktop/ff951640) jest kolekcją zasobów — Grupa bibliotek DLL, klasy okien, serwery COM, biblioteki typów lub interfejsy — dostępne dla aplikacji do użycia w czasie wykonywania. Główną zaletą ponowne utworzenie pakietu bibliotek DLL w zestawach jest wiele wersji zestawy mogą być używane przez aplikacje w tym samym czasie, a istnieje możliwość zestawy aktualnie zainstalowanej usługi w przypadku wersji aktualizacji.  
  
 Aplikacji Visual C++ mogą używać jednego lub kilku bibliotek DLL w różnych części aplikacji. W czasie wykonywania biblioteki DLL są ładowane do głównego procesu i kod wymagany jest wykonywany. Aplikacja korzysta z systemu operacyjnego można zlokalizować żądanego bibliotek DLL, zrozumieć, co inne zależne biblioteki DLL muszą zostać załadowany, a następnie je razem z żądanej biblioteki DLL. W wersjach systemów operacyjnych Windows starszych niż Windows XP, Windows Server 2003 i Windows Vista modułu ładującego systemu operacyjnego wyszukiwanie zależne biblioteki dll w folderze lokalnym aplikacji lub inny folder określony w ścieżce systemowej. W systemie Windows XP, Windows Server 2003 i Windows Vista modułu ładującego systemu operacyjnego można także wyszukać zależnej biblioteki DLL przy użyciu [manifestu](http://msdn.microsoft.com/library/windows/desktop/aa375365) plik i poszukaj side-by-side zestawy, które zawierają te biblioteki dll.  
  
 Domyślnie podczas tworzenia biblioteki DLL z programem Visual Studio ma [manifest aplikacji](http://msdn.microsoft.com/library/windows/desktop/aa374191) osadzony jako zasób RT_MANIFEST o identyfikatorze równa 2. Podobnie jak w przypadku pliku wykonywalnego tego manifestu opisano zależności tę bibliotekę DLL na innych zestawów. Przy założeniu, że plik DLL, który nie jest częścią zestawu side-by-side i aplikacje, które są zależne od tej biblioteki DLL nie będą używać manifestu aplikacji do ładowania, ale zamiast tego zależą od modułu ładującego systemu operacyjnego, aby znaleźć tę bibliotekę DLL na ścieżce systemowej.  
  
> [!NOTE]
>  Jest ważne w przypadku bibliotekę DLL, która używa manifest aplikacji ma manifestu osadzony jako zasób o identyfikatorze równa 2. Jeśli plik DLL, który dynamicznie został załadowany w czasie wykonywania (na przykład za pomocą [LoadLibrary](http://msdn.microsoft.com/library/windows/desktop/ms684175) funkcji), zależne zestawy określona w manifeście DLL ładuje modułu ładującego systemu operacyjnego. Manifest aplikacji zewnętrznych dla bibliotek DLL nie jest sprawdzana podczas `LoadLibrary` wywołania. Jeśli manifest nie jest zagnieżdżony, moduł ładujący mogą próbować niepowodzeniem zestawów zależnych Znajdź można znaleźć lub załadować niepoprawny wersje zestawów.  
  
 Jeden lub kilka związane z bibliotek DLL może być pakietach w ramach zestawu side-by-side z odpowiednią [manifest zestawu](http://msdn.microsoft.com/library/windows/desktop/aa374219), która opisuje pliki, które tworzą zestaw, a także zależność zestawu na inne side-by-side zestawy.  
  
> [!NOTE]
>  Zestaw zawiera jedną bibliotekę DLL, zalecane jest osadzanie manifestu zestawu w tej biblioteki DLL jako zasób o identyfikatorze równą 1 i przypisz zestaw prywatny taką samą nazwę jak biblioteki DLL. Na przykład, jeśli nazwa biblioteki DLL jest mylibrary.dll, wartość atrybutu nazwy są używane w \<assemblyIdentity > element manifest może być również MojaBiblioteka. W niektórych przypadkach, gdy biblioteka ma rozszerzeniem innym niż dll (na przykład projektu kontrolki ActiveX MFC tworzy bibliotekę ocx) można utworzyć manifestu zestawu zewnętrznych. W takim przypadku nazwa zestawu i jego manifestu musi być inna niż nazwa biblioteki dll (na przykład, MyAssembly, MyAssembly.manifest i mylibrary.ocx). Jednak nadal zaleca się zmienić takie bibliotek extension.dll i osadzania manifestu jako zasób będzie zmniejszenie kosztów obsługi przyszłych tego zestawu. Aby uzyskać więcej informacji dotyczących sposobu wyszukiwania przez zestawy prywatne system operacyjny, zobacz [sekwencji wyszukiwania zestawu](http://msdn.microsoft.com/library/windows/desktop/aa374224).  
  
 Ta zmiana może zezwolić wdrożenia odpowiednie dll jako [zestaw prywatny](http://msdn.microsoft.com/library/windows/desktop/aa370850) w lokalnym folderze aplikacji lub jako [zestaw udostępnionego](http://msdn.microsoft.com/library/windows/desktop/aa371839) w pamięci podręcznej zestawów folderze WinSxS. Kilka kroków musi występować w celu osiągnięcia poprawne zachowanie tego nowego zestawu; zostały one opisane w [wytyczne dotyczące tworzenia Side-by-side zestawy](http://msdn.microsoft.com/library/windows/desktop/aa375155). Zestaw jest poprawnie przypisany można wdrożyć jako albo udostępnionego lub prywatnej zestawu razem z aplikacją, która zależy od niego. Podczas instalowania zestawy side-by-side jako zestaw udostępnionego, może albo wykonaj wytycznych przedstawionych w [instalowanie zestawy Win32 dla udostępniania Side-by-Side, w systemie Windows XP](http://msdn.microsoft.com/library/windows/desktop/aa369532) lub użyj [scalania modułów](http://msdn.microsoft.com/library/windows/desktop/aa369820). Podczas instalowania zestawy side-by-side jako zestaw prywatny, możesz może po prostu skopiuj odpowiednie manifestu biblioteki DLL, zasobów i zestawu jako część procesu instalacji do folderu lokalnego aplikacji na komputerze docelowym zapewnienie, że ten zestaw może być znalezione przez moduł ładujący w czasie wykonywania (zobacz [sekwencji wyszukiwania zestawu](http://msdn.microsoft.com/library/windows/desktop/aa374224)). Innym sposobem jest użycie [Instalatora Windows](http://msdn.microsoft.com/library/windows/desktop/cc185688) i trzymać się wskazówek podanych w [instalowanie zestawów Win32 prywatnego użytku aplikacji w systemie Windows XP](http://msdn.microsoft.com/library/windows/desktop/aa369534).  
  
## <a name="see-also"></a>Zobacz też  
 [Przykłady wdrożeń](../ide/deployment-examples.md)   
 [Tworzenie C/C++ izolowanych](../build/building-c-cpp-isolated-applications.md)   
 [Kompilowanie aplikacji izolowanych C/C++ oraz aplikacji wykonywanych równocześnie](../build/building-c-cpp-isolated-applications-and-side-by-side-assemblies.md)