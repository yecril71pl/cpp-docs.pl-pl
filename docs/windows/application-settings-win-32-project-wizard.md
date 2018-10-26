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
ms.openlocfilehash: 7342e8cfb95e8e443631563499a84fd7bd6579a1
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50080705"
---
# <a name="application-settings-win-32-project-wizard"></a>Ustawienia aplikacji, kreator projektów Win 32

Ta strona kreatora umożliwia ustawianie opcji Projekt systemu Win32.

## <a name="application-type"></a>Typ aplikacji

Tworzy typ określonej aplikacji.

|Opcja|Opis|
|------------|-----------------|
|**Aplikacja konsolowa**|Tworzy aplikację konsoli. Programy konsoli są tworzone z użyciem [funkcje konsoli](https://msdn.microsoft.com/library/ms813137.aspx), które zapewniają obsługę tryb znakowy w konsoli systemu windows. Visual C++ [biblioteki wykonawczej](../c-runtime-library/c-run-time-library-reference.md) również podać dane wyjściowe i dane wejściowe z okna konsoli za pomocą funkcji standardowych operacji We/Wy, takich jak `printf_s()` i `scanf_s()`. Aplikacja konsolowa nie ma graficznego interfejsu użytkownika. On kompilowany na plik .exe i mogą być uruchamiane jako autonomiczną aplikację z poziomu wiersza polecenia.<br /><br /> Możesz dodać obsługę MFC i ATL do aplikacji konsoli.|
|**Aplikacja Windows**|Powoduje utworzenie programu systemu Win32. Programu systemu Win32 jest aplikacja pliku wykonywalnego (EXE) w języku C lub C++, tworzenie graficznego interfejsu użytkownika przy użyciu wywołania funkcji API Win32.<br /><br /> Nie można dodać MFC lub ATL Obsługa aplikacji Windows.|
|**DLL**|Tworzy Win32 biblioteki dołączanej (dynamicznie DLL). Biblioteka DLL systemu Win32 jest plik binarny, napisany w języku C lub C++, który używa wywołania funkcji API Win32, a nie do klas MFC i który działa jako współdzielona biblioteka funkcji, które mogą być używane jednocześnie przez wiele aplikacji.<br /><br /> Nie można dodać MFC lub ATL pomocy technicznej dla aplikacji DLL. Można wskazać, że biblioteka DLL eksportuje symboli.|
|**Biblioteka statyczna**|Tworzy bibliotekę statyczną. Biblioteka statyczna jest plikiem zawierającym obiektów i ich funkcje i dane, który stanowi łącze do tego programu, podczas kompilowania pliku wykonywalnego. W tym temacie opisano sposób tworzenia plikach startowych i [właściwości projektu](../ide/property-pages-visual-cpp.md) dla biblioteki statycznej. Plik biblioteki statycznej zapewnia następujące korzyści:<br /><br />Biblioteka statyczna Win32 jest przydatne w przypadku aplikacji, którą pracujesz nad wywołań interfejsu API Win32, a nie do klas MFC.<br />— Proces łączenia jest taki sam, czy w pozostałej części aplikacji Windows są zapisywane w języku C lub C++.<br />— Biblioteka statyczna możesz połączyć program oparty na bibliotece MFC lub program innego typu niż MFC.|

## <a name="additional-options"></a>Dodatkowe opcje

Definiuje pomocy technicznej i opcje dla aplikacji, w zależności od jego typu.

|Opcja|Opis|
|------------|-----------------|
|**Pusty projekt**|Określa, że pliki projektu są puste. Jeśli masz zestaw plików kodu źródłowego (na przykład plików .cpp, pliki nagłówkowe, ikony, paski narzędzi, okna dialogowe i tak dalej) i chcesz utworzyć projekt w środowisku programowania Visual C++, użytkownik musi najpierw utwórz pusty projekt, a następnie dodaj pliki do projektu.<br /><br /> Zaznacz to pole wyboru jest niedostępny dla projektów biblioteki statycznej.|
|**Eksportuj symbole**|Określa, że projekt DLL eksportuje symboli.|
|**Prekompilowany plik nagłówkowy**|Określa, że projekt biblioteki statycznej używa wstępnie skompilowanym nagłówkiem.|
|Sprawdza, czy cykl projektowania zabezpieczeń (SDL)|Aby uzyskać więcej informacji na temat SDL, zobacz [wskazówek dotyczących procesu cykl projektowania zabezpieczeń (SDL)](../build/reference/sdl-enable-additional-security-checks.md)|

## <a name="add-support-for"></a>Dodano obsługę

Dodano obsługę jednej z bibliotek dostarczane w programie Visual C++.

|Opcja|Opis|
|------------|-----------------|
|**ATL**|Kompilacje do obsługi projektu dla klas w Active Template Library (ATL). Win32 console tylko dla aplikacji.<br /><br /> **Uwaga** tej opcji nie oznacza Obsługa dodawania obiektów ATL za pomocą ATL kodu kreatorów. Obiekty ATL można dodawać tylko do projektów ATL lub projektów MFC z biblioteki ATL pomocy technicznej.|
|**MFC**|Kompilacje do obsługi projektu biblioteki Microsoft Foundation Class (MFC). Aplikacje konsoli Win32 i tylko w przypadku bibliotek statycznych.|

## <a name="see-also"></a>Zobacz też

[Kreator aplikacji Win32](../windows/win32-application-wizard.md)