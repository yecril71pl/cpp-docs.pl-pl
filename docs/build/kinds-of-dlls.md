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

Ten temat zawiera informacje ułatwiające określenie rodzaju biblioteki DLL do utworzenia.

## <a name="different-kinds-of-dlls-available"></a><a name="_core_the_different_kinds_of_dlls_available_with_visual_c.2b2b"></a>Dostępne różne rodzaje bibliotek DLL

Za pomocą programu Visual Studio można tworzyć biblioteki DLL win32 w języku C lub C++, które nie używają biblioteki Microsoft Foundation Class (MFC). Można utworzyć projekt dll innych niż MFC za pomocą Kreatora aplikacji Win32.

Sama biblioteka MFC jest dostępna w bibliotekach łączy statycznych lub w wielu bibliotekach DLL za pomocą Kreatora bibliotek DLL MFC. Jeśli biblioteka DLL używa MFC, visual studio obsługuje trzy różne scenariusze rozwoju biblioteki DLL:

- Tworzenie zwykłej biblioteki DLL MFC, która statycznie łączy MFC

- Tworzenie zwykłej biblioteki DLL MFC, która dynamicznie łączy MFC

- Tworzenie biblioteki DLL rozszerzenia MFC, która zawsze dynamicznie łączy MFC

### <a name="what-do-you-want-to-know-more-about"></a>O czym chcesz wiedzieć więcej?

- [Biblioteki DLL inne niż MFC: omówienie](non-mfc-dlls-overview.md)

- [Zwykłe biblioteki DLL MFC połączone statycznie z MFC](regular-dlls-statically-linked-to-mfc.md)

- [Zwykłe biblioteki DLL MFC połączone dynamicznie z MFC](regular-dlls-dynamically-linked-to-mfc.md)

- [Biblioteki DLL rozszerzeń MFC: omówienie](extension-dlls-overview.md)

- [Jakiego rodzaju biblioteki DLL użyć](#_core_which_kind_of_dll_to_use)

## <a name="deciding-which-kind-of-dll-to-use"></a><a name="_core_which_kind_of_dll_to_use"></a>Decydowanie, jakiego rodzaju biblioteki DLL użyć

Jeśli biblioteka DLL nie używa MFC, użyj programu Visual Studio do tworzenia biblioteki DLL w wersji 32 innych niż MFC. Łączenie biblioteki DLL z MFC (statycznie lub dynamicznie) zajmuje znaczne miejsce na dysku i pamięci. Nie należy łączyć się z MFC, chyba że biblioteka DLL faktycznie używa MFC.

Jeśli biblioteka DLL będzie używać MFC i będą używane przez aplikacje MFC lub innych niż MFC, należy utworzyć regularne MFC DLL, który dynamicznie łączy się z MFC lub regularne MFC DLL, który statycznie łączy się z MFC. W większości przypadków prawdopodobnie chcesz użyć zwykłej biblioteki DLL MFC, która dynamicznie łączy się z MFC, ponieważ rozmiar pliku biblioteki DLL będzie znacznie mniejszy, a oszczędności w pamięci wynikające z używania udostępnionej wersji MFC mogą być znaczące. Jeśli statycznie łącze do MFC, rozmiar pliku biblioteki DLL będzie większy i potencjalnie zajmie dodatkową pamięć, ponieważ ładuje własną kopię prywatną kodu biblioteki MFC.

Tworzenie biblioteki DLL, która dynamicznie łączy się z MFC jest szybsze niż tworzenie biblioteki DLL, która statycznie łączy się z MFC, ponieważ nie jest konieczne łączenie MFC się. Jest to szczególnie prawdziwe w debugowania kompilacji, gdzie konsolidator musi kompaktowy informacji debugowania. Łącząc się z biblioteką DLL, która już zawiera informacje debugowania, jest mniej informacji debugowania do kompaktowania w ramach biblioteki DLL.

Jedną z wad dynamicznego łączenia z MFC jest to, że należy dystrybuować udostępnione biblioteki DLL Mfcx0.dll i Msvcrxx.dll (lub podobne pliki) z biblioteką DLL. Biblioteki DLL MFC są swobodnie redystrybucyjne, ale nadal należy zainstalować biblioteki DLL w programie instalacyjnym. Ponadto należy wysłać plik Msvcrxx.dll, który zawiera bibliotekę czasu wykonywania C, która jest używana zarówno przez program, jak i przez same biblioteki DLL MFC.

Jeśli biblioteka DLL będzie używana tylko przez pliki wykonywalne MFC, masz wybór między tworzeniem zwykłej biblioteki DLL MFC lub biblioteki DLL rozszerzenia MFC. Jeśli biblioteka DLL implementuje klasy wielokrotnego użytku pochodzące z istniejących klas MFC lub trzeba przekazać obiekty pochodne MFC między aplikacją a biblioteką DLL, należy utworzyć bibliotekę DLL rozszerzenia MFC.

Jeśli biblioteka DLL dynamicznie łączy się z MFC, biblioteki DLL MFC mogą być ponownie redystrybuowane z biblioteką DLL. Ta architektura jest szczególnie przydatna do udostępniania biblioteki klas między wieloma plikami wykonywalnymi w celu zaoszczędzenia miejsca na dysku i zminimalizowania użycia pamięci.

### <a name="what-do-you-want-to-know-more-about"></a>O czym chcesz wiedzieć więcej?

- [Biblioteki DLL inne niż MFC: omówienie](non-mfc-dlls-overview.md)

- [Zwykłe biblioteki DLL MFC połączone statycznie z MFC](regular-dlls-statically-linked-to-mfc.md)

- [Zwykłe biblioteki DLL MFC połączone dynamicznie z MFC](regular-dlls-dynamically-linked-to-mfc.md)

- [Biblioteki DLL rozszerzeń MFC: omówienie](extension-dlls-overview.md)

## <a name="see-also"></a>Zobacz też

[Tworzenie bibliotek DLL języka C/C++ w programie Visual Studio](dlls-in-visual-cpp.md)
