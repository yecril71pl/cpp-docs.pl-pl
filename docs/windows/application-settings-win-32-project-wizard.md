---
title: Ustawienia aplikacji, Kreator projektów Win 32 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.appwiz.win32.appset
dev_langs:
- C++
helpviewer_keywords:
- application settings [C++]
- Win32 Project Wizard, application settings
ms.assetid: d6b818f0-9b23-4793-a6c5-df1c8c594bad
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 55ae50d849a67da69cde6a9c4b1529c34ee4b428
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
---
# <a name="application-settings-win-32-project-wizard"></a>Ustawienia aplikacji, kreator projektów Win 32
Aby ustawić opcje projektu Win32, użyj tej strony kreatora.  
  
 **Typ aplikacji**  
 Tworzy typ określonej aplikacji.  
  
|Opcja|Opis|  
|------------|-----------------|  
|**Aplikacji konsoli**|Tworzy aplikację konsoli. Programy konsoli są tworzone z [funkcje konsoli](https://msdn.microsoft.com/en-us/library/ms813137.aspx), które zapewniają obsługę tryb znakowy w konsoli systemu windows. Visual C++ [biblioteki wykonawczej](../c-runtime-library/c-run-time-library-reference.md) również podać dane wyjściowe i dane wejściowe z okna konsoli standardowe funkcje We/Wy, takich jak **printf_s()** i **scanf_s()**. Aplikacja konsolowa nie ma graficznego interfejsu użytkownika. Kompiluje do pliku .exe, a może działać jako aplikacja autonomiczna z wiersza polecenia.<br /><br /> Możesz dodać obsługę MFC i ATL aplikacji konsoli.|  
|**Aplikacja systemu Windows**|Tworzy programu systemu Win32. Programu systemu Win32 jest aplikacją wykonywalną (EXE) napisana C lub C++ do utworzenia graficznego interfejsu użytkownika przy użyciu wywołania interfejsu API systemu Win32.<br /><br /> Nie można dodać MFC lub ATL wsparcie dla aplikacji systemu Windows.|  
|**DLL**|Tworzy Win32 biblioteki dołączanej (dynamicznie DLL). Biblioteki DLL systemu Win32 jest plikiem binarnym, napisana C lub C++, która używa wywołania funkcji API Win32, a nie do klas MFC i który pełni rolę biblioteki udostępnionej funkcji, które mogą być używane równocześnie przez wiele aplikacji.<br /><br /> Nie można dodać MFC lub ATL wsparcie dla aplikacji DLL. Można wskazać, że plik DLL, który eksportuje symboli.|  
|**Biblioteka statyczna**|Tworzy bibliotekę statyczną. Biblioteka statyczna jest plik zawierający obiekty i ich funkcji i danych, który stanowi łącze do tego programu, podczas tworzenia pliku wykonywalnego. W tym temacie wyjaśniono, jak utworzyć pliki początkowe i [właściwości projektu](../ide/property-pages-visual-cpp.md) dla biblioteki statycznej. Plik biblioteki statycznej zapewnia następujące korzyści:<br /><br /> -Win32 biblioteki statycznej jest przydatne w przypadku aplikacji, w którym pracujesz na wywołań funkcji API Win32, a nie do klas MFC.<br />-Proces łączenia jest taka sama czy rest aplikacji systemu Windows są zapisywane w języku C lub C++.<br />— Biblioteka statyczna możesz połączyć programu opartego na MFC lub program innego typu niż MFC.|  
  
 **Dodatkowe opcje**  
 Definiuje pomocy technicznej i opcje dla aplikacji, w zależności od jego typu.  
  
|Opcja|Opis|  
|------------|-----------------|  
|**Pusty projekt**|Określa, czy pliki projektu są puste. Jeśli masz zestaw plików kodu źródłowego (na przykład pliki .cpp, pliki nagłówkowe, ikony, paski narzędzi, okna dialogowe i tak dalej) i chcesz utworzyć projekt w środowisku projektowym Visual C++, należy najpierw utworzyć pusty projekt, a następnie dodaj pliki do projektu.<br /><br /> Ta opcja jest niedostępna dla projektów biblioteki statycznej.|  
|**Eksportowanie symboli**|Określa, że projekt DLL eksportuje symboli.|  
|**Prekompilowanego nagłówka**|Określa, że projekt biblioteki statycznej używa wstępnie skompilowanym nagłówkiem.|  
|Sprawdza Security Development Lifecycle (SDL)|Aby uzyskać więcej informacji na temat SDL, zobacz [wskazówek dotyczących procesu Microsoft Security Development Lifecycle (SDL)](../build/reference/sdl-enable-additional-security-checks.md)|  
  
 **Dodawanie obsługi**  
 Dodaj obsługę jednej z bibliotek dostarczanych w programie Visual C++.  
  
|Opcja|Opis|  
|------------|-----------------|  
|**ATL**|Tworzy w projekcie obsługę klas w Active Template Library (ATL). Win32 konsoli tylko dla aplikacji.<br /><br /> **Uwaga** ta opcja nie wskazuje Obsługa dodawania obiektów ATL za pomocą biblioteki ATL kodu kreatorów. Obiekty ATL można dodawać tylko do projektów ATL lub projekty MFC z biblioteki ATL obsługują.|  
|**MFC**|Kompilacje do obsługi projektu biblioteki Microsoft Foundation Class (MFC). Aplikacje konsoli Win32 i tylko w przypadku bibliotek statycznych.|  
  
## <a name="see-also"></a>Zobacz też  
 [Kreator aplikacji Win32](../windows/win32-application-wizard.md)   
