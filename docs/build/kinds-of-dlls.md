---
title: Rodzaje bibliotek DLL
ms.date: 11/04/2016
helpviewer_keywords:
- MFC DLLs [C++], types
- DLLs [C++], types
- DLLs [C++], MFC
ms.assetid: f6a30db9-6138-4b2c-90cc-a17855e499a6
ms.openlocfilehash: daf042f742a9c4b7757813fc73eeb4b6d1a87413
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50441122"
---
# <a name="kinds-of-dlls"></a>Rodzaje bibliotek DLL

Ten temat zawiera informacje pomocne w określeniu rodzaju DLL do kompilacji.

##  <a name="_core_the_different_kinds_of_dlls_available_with_visual_c.2b2b"></a> Różne rodzaje dostępnych bibliotek DLL

Przy użyciu języka Visual C++, można kompilować dll Win32 w C lub C++, które nie używają biblioteki Microsoft Foundation Class (MFC). Można utworzyć projekt DLL bez MFC za pomocą Kreatora aplikacji Win32.

Sama biblioteka MFC jest dostępna, w bibliotekach łącza statycznego lub w szeregu bibliotek DLL, przy użyciu Kreatora MFC DLL. Jeśli biblioteka DLL wykorzystuje MFC, Visual C++ obsługuje trzy różne scenariusze rozwoju biblioteki DLL:

- Kompilowanie zwykłej biblioteki MFC DLL, która statycznie łączy się z MFC

- Kompilowanie zwykłej biblioteki MFC DLL, która dynamicznie łączy się z MFC

- Kompilowanie rozszerzenia MFC biblioteki DLL, która zawsze dynamiczne łączy biblioteki MFC

### <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej na temat?

- [Biblioteki DLL inne niż MFC: omówienie](../build/non-mfc-dlls-overview.md)

- [Regularne biblioteki DLL MFC połączone statycznie z MFC](../build/regular-dlls-statically-linked-to-mfc.md)

- [Regularne biblioteki DLL MFC połączone dynamicznie z MFC](../build/regular-dlls-dynamically-linked-to-mfc.md)

- [Biblioteki DLL rozszerzeń MFC: omówienie](../build/extension-dlls-overview.md)

- [Którego rodzaju DLL użyć](#_core_which_kind_of_dll_to_use)

##  <a name="_core_which_kind_of_dll_to_use"></a> Decydowanie którego rodzaju biblioteki DLL użyć

Jeśli biblioteka DLL nie używa MFC, należy użyć Visual C++ do tworzenia nie - MFC Win32 DLL. Łączenie MFC DLL (statycznie lub dynamicznie) zajmuje znacznej ilości miejsca i pamięci. Nie należy dodawać łączy do MFC, chyba że Twój DLL faktycznie korzysta z MFC.

Jeśli biblioteka DLL będzie używać MFC i będą używane przez aplikacje MFC lub innego typu niż MFC, należy utworzyć zwykłej biblioteki MFC DLL, która łączy dynamicznie do MFC albo zwykłej biblioteki MFC DLL, która statycznie łączy się MFC. W większości przypadków prawdopodobnie chcesz użyć zwykłej biblioteki MFC DLL, która dynamicznie łączy z MFC, ponieważ rozmiar pliku biblioteki dll będzie znacznie mniejszy i oszczędności pamięci wynikające z wykorzystania udostępnionej wersja MFC mogą być znaczące. Jeśli połączysz się statycznie z MFC, rozmiar pliku biblioteki dll będzie większa i potencjalnie zajmie dodatkową pamięć, ponieważ ładuje własną prywatną kopię kodu biblioteki MFC.

Kompilowanie biblioteki DLL, która łączy dynamicznie MFC jest szybsza niż kompilowanie biblioteki DLL, która statycznie łączy się MFC, ponieważ nie jest konieczne samo łąćzneie z MFC. Jest to szczególnie istotne w debugowanych kompilacjach, gdzie konsolidator musi zmniejszyć informację debugowania. Łącząc się z biblioteką DLL, która już zawiera informacje o debugowaniu, jest mniej informacji debugowania do kompaktowania w bibliotece DLL.

Jedną wadą do MFC jest konieczność rozłożenia udostępnionych bibliotek DLL Mfcx0.dll i Msvcrxx.dll (lub podobnych plików) w z biblioteką DLL. Biblioteki MFC DLL można dowolnie rozprowadzać, ale trzeba mimo to zainstalować biblioteki dll w programie Instalatora. Ponadto należy dostarczyć plik Msvcrxx.dll, który zawiera biblioteki wykonawczej C, który jest używany zarówno przez program i same biblioteki MFC DLL.

Jeśli biblioteka DLL będzie używana tylko przez pliki wykonywalne MFC, możesz dokonać wyboru między kompilacją regularnej biblioteki MFC DLL lub biblioteki DLL rozszerzenia MFC. Jeśli biblioteka DLL implementuje klasy wielokrotnego użytku pochodzące z istniejących klas MFC lub należy przekazać obiekty pochodzące z MFC między aplikacją a biblioteki DLL, należy utworzyć rozszerzenia MFC biblioteki DLL.

Jeśli biblioteka DLL dynamicznie łączy z MFC, biblioteki MFC dll mogą być rozdystrybuowane z biblioteką DLL. Ta architektura jest szczególnie pomocna przy udostępnianiu biblioteki klas, aby zaoszczędzić miejsce na dysku i zminimalizować użycie pamięci na wielu plikom wykonawczym.

Przed wersją 4.0, Visual C++ obsługiwał tylko dwa rodzaje bibliotek DLL, które używały MFC: Usrdll i Afxdll. Regularne biblioteki DLL MFC połączone statycznie z MFC mają takie same charakterystyki jak dawny USRDLL. Rozszerzone dll MFC mają takie same charakterystyki jak dawne biblioteki Afxdll.

### <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej na temat?

- [Biblioteki DLL inne niż MFC: omówienie](../build/non-mfc-dlls-overview.md)

- [Regularne biblioteki DLL MFC połączone statycznie z MFC](../build/regular-dlls-statically-linked-to-mfc.md)

- [Regularne biblioteki DLL MFC połączone dynamicznie z MFC](../build/regular-dlls-dynamically-linked-to-mfc.md)

- [Biblioteki DLL rozszerzeń MFC: omówienie](../build/extension-dlls-overview.md)

## <a name="see-also"></a>Zobacz też

[Biblioteki DLL w programie Visual C++](../build/dlls-in-visual-cpp.md)