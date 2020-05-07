---
title: Rodzaje bibliotek DLL
ms.date: 05/06/2019
helpviewer_keywords:
- MFC DLLs [C++], types
- DLLs [C++], types
- DLLs [C++], MFC
ms.assetid: f6a30db9-6138-4b2c-90cc-a17855e499a6
ms.openlocfilehash: dae44d2dd39597420ce2a2c4e1642e8a7f0784e2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328499"
---
# <a name="kinds-of-dlls"></a>Rodzaje bibliotek DLL

Ten temat zawiera informacje ułatwiające określenie rodzaju biblioteki DLL do skompilowania.

## <a name="different-kinds-of-dlls-available"></a><a name="_core_the_different_kinds_of_dlls_available_with_visual_c.2b2b"></a>Dostępne są różne rodzaje bibliotek DLL

Za pomocą programu Visual Studio można tworzyć biblioteki Win32 DLL w języku C lub C++, które nie korzystają z biblioteki Microsoft Foundation Class (MFC). Można utworzyć projekt z biblioteką DLL bez MFC za pomocą Kreatora aplikacji Win32.

Sama Biblioteka MFC jest dostępna w bibliotekach dołączanych statycznie lub w wielu bibliotekach DLL przy użyciu kreatora MFC DLL. Jeśli biblioteka DLL korzysta z MFC, program Visual Studio obsługuje trzy różne scenariusze tworzenia bibliotek DLL:

- Tworzenie zwykłej biblioteki MFC DLL, która statycznie łączy MFC

- Tworzenie zwykłej biblioteki MFC DLL, która dynamicznie łączy MFC

- Kompilowanie biblioteki DLL rozszerzenia MFC, która zawsze dynamicznie łączy MFC

### <a name="what-do-you-want-to-know-more-about"></a>Jak chcesz dowiedzieć się więcej?

- [Biblioteki DLL inne niż MFC: omówienie](non-mfc-dlls-overview.md)

- [Zwykłe biblioteki DLL MFC połączone statycznie z MFC](regular-dlls-statically-linked-to-mfc.md)

- [Zwykłe biblioteki DLL MFC połączone dynamicznie z MFC](regular-dlls-dynamically-linked-to-mfc.md)

- [Biblioteki DLL rozszerzeń MFC: omówienie](extension-dlls-overview.md)

- [Jakiego rodzaju biblioteki DLL użyć](#_core_which_kind_of_dll_to_use)

## <a name="deciding-which-kind-of-dll-to-use"></a><a name="_core_which_kind_of_dll_to_use"></a>Wybór rodzaju biblioteki DLL do użycia

Jeśli biblioteka DLL nie korzysta z MFC, należy użyć programu Visual Studio do utworzenia biblioteki DLL Win32 innej niż MFC. Łączenie biblioteki DLL z MFC (statycznie lub dynamicznie) zajmuje dużo miejsca na dysku i pamięci. Nie należy łączyć z MFC, chyba że biblioteka DLL rzeczywiście używa MFC.

Jeśli biblioteka DLL będzie używać MFC i będzie używana przez aplikacje MFC lub inne niż MFC, należy utworzyć zwykłą bibliotekę MFC DLL, która łączy dynamicznie z MFC lub zwykłą biblioteką DLL MFC, która statycznie łączy się z MFC. W większości przypadków prawdopodobnie chcesz użyć zwykłej biblioteki MFC DLL, która dynamicznie łączy się z MFC, ponieważ rozmiar pliku biblioteki DLL będzie znacznie mniejszy i oszczędności w pamięci z użyciem udostępnionej wersji MFC mogą być istotne. Jeśli statycznie łączy się z MFC, rozmiar pliku biblioteki DLL będzie większy i potencjalnie zajmuje dodatkową pamięć, ponieważ ładuje własną prywatną kopię kodu biblioteki MFC.

Kompilowanie biblioteki DLL, która dynamicznie łączy się z MFC jest szybsze niż Kompilowanie biblioteki DLL, która statycznie łączy się z MFC, ponieważ nie jest konieczne łączenie MFC. Jest to szczególnie prawdziwe w kompilacjach debugowania, gdzie konsolidator musi kompaktować informacje debugowania. Łącząc się z biblioteką DLL, która zawiera już informacje o debugowaniu, informacje debugowania są mniejsze do kompaktowania w bibliotece DLL.

Jedną z wadą dynamicznego łączenia z klasą MFC jest konieczność dystrybucji udostępnionych bibliotek DLL MFCx0. dll i Msvcrxx. dll (lub podobnych plików) z biblioteką DLL. Biblioteki MFC DLL są swobodnie rozpowszechniane, ale nadal trzeba zainstalować biblioteki DLL w programie instalacyjnym. Ponadto należy dostarczyć plik Msvcrxx. dll, który zawiera bibliotekę wykonawczą C, która jest używana zarówno przez program, jak i biblioteki DLL MFC.

Jeśli biblioteka DLL będzie używana tylko przez pliki wykonywalne MFC, istnieje możliwość utworzenia zwykłej biblioteki MFC DLL lub biblioteki DLL rozszerzenia MFC. Jeśli biblioteka DLL implementuje klasy wielokrotnego użytku pochodzące z istniejących klas MFC lub należy przekazać obiekty pochodne MFC między aplikacją a biblioteką DLL, należy utworzyć bibliotekę DLL rozszerzenia MFC.

Jeśli biblioteka DLL łączy się dynamicznie z MFC, biblioteki MFC mogą być rozpowszechniane za pomocą biblioteki DLL. Ta architektura jest szczególnie przydatna w przypadku udostępniania biblioteki klas między wieloma plikami wykonywalnymi w celu zaoszczędzenia miejsca na dysku i zminimalizowania użycia pamięci.

### <a name="what-do-you-want-to-know-more-about"></a>Jak chcesz dowiedzieć się więcej?

- [Biblioteki DLL inne niż MFC: omówienie](non-mfc-dlls-overview.md)

- [Zwykłe biblioteki DLL MFC połączone statycznie z MFC](regular-dlls-statically-linked-to-mfc.md)

- [Zwykłe biblioteki DLL MFC połączone dynamicznie z MFC](regular-dlls-dynamically-linked-to-mfc.md)

- [Biblioteki DLL rozszerzeń MFC: omówienie](extension-dlls-overview.md)

## <a name="see-also"></a>Zobacz też

[Tworzenie bibliotek DLL C/C++ w programie Visual Studio](dlls-in-visual-cpp.md)
