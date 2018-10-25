---
title: Wersje biblioteki MFC | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 1/09/2018
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- class libraries [MFC], building versions
- version information [MFC], MFC library
- MFC class library
- MFC class library, building
- MFC libraries
- MFC, library versions
- libraries [MFC], versions
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9a077cd90055a17f9aff71d67d2cb9a511a1caf0
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50078040"
---
# <a name="mfc-library-versions"></a>Wersje biblioteki MFC

Biblioteka MFC jest dostępna w wersji obsługujących jednobajtowe ANSI i znaku wielobajtowego zestawu kodu (MBCS), a także wersje, które obsługują znaki Unicode (zakodowanymi w formacie UTF-16LE, zestaw znaków Windows native). Każda wersja MFC jest dostępna jako biblioteka statyczna lub współdzielonej bibliotece DLL. Istnieje również mniejszych wersji statyczne biblioteki MFC, która powoduje, że formantów MFC w oknach dialogowych dla aplikacji, które są bardzo wrażliwe na wielkość i nie wymagają tych kontrolek. Biblioteki MFC są dostępne w obu debugowania i wydania wersji obsługiwane architektury, które zawierają x86 x64 i procesorów ARM. Możesz utworzyć obie aplikacje (pliki .exe) i biblioteki DLL przy użyciu dowolnej wersji biblioteki MFC. Istnieje również zestaw bibliotek MFC, skompilowany powiązania z kodu zarządzanego. Współdzielone MFC DLL obejmują numer wersji, aby wskazać zgodność binarną biblioteki.

## <a name="automatic-linking-of-mfc-library-versions"></a>Automatyczne łączenie wersji biblioteki MFC

W plikach nagłówkowych MFC automatycznie określić poprawną wersję biblioteki MFC, aby utworzyć łącze, na podstawie wartości zdefiniowane w środowisku kompilacji. W plikach nagłówkowych MFC Dodaj dyrektywy kompilatora poinstruowanie konsolidator łącze w określonej wersji biblioteki MFC.

Na przykład AFX. Plik nagłówkowy H powoduje, że konsolidator łącze w pełnej statyczne, ograniczone statyczne lub udostępnione wersja dll biblioteki MFC; ANSI/MBCS lub Unicode wersji; i wersja debugowania lub wersji detalicznej, w zależności od konfiguracji kompilacji:

```cpp
#ifndef _AFXDLL
    #ifdef _AFX_NO_MFC_CONTROLS_IN_DIALOGS
        #ifdef _DEBUG
            #pragma comment(lib, "afxnmcdd.lib")
        #else
            #pragma comment(lib, "afxnmcd.lib")
        #endif
        #pragma comment(linker, "/include:__afxNoMFCControlSupportInDialogs")
        #pragma comment(linker, "/include:__afxNoMFCControlContainerInDialogs")
    #endif
    #ifndef _UNICODE
        #ifdef _DEBUG
            #pragma comment(lib, "nafxcwd.lib")
        #else
            #pragma comment(lib, "nafxcw.lib")
        #endif
    #else
        #ifdef _DEBUG
            #pragma comment(lib, "uafxcwd.lib")
        #else
            #pragma comment(lib, "uafxcw.lib")
        #endif
    #endif
#else
    #ifndef _UNICODE
        #ifdef _DEBUG
            #pragma comment(lib, "mfc" _MFC_FILENAME_VER "d.lib")
            #pragma comment(lib, "mfcs" _MFC_FILENAME_VER "d.lib")
        #else
            #pragma comment(lib, "mfc" _MFC_FILENAME_VER ".lib")
            #pragma comment(lib, "mfcs" _MFC_FILENAME_VER ".lib")
        #endif
    #else
        #ifdef _DEBUG
            #pragma comment(lib, "mfc" _MFC_FILENAME_VER "ud.lib")
            #pragma comment(lib, "mfcs" _MFC_FILENAME_VER "ud.lib")
        #else
            #pragma comment(lib, "mfc" _MFC_FILENAME_VER "u.lib")
            #pragma comment(lib, "mfcs" _MFC_FILENAME_VER "u.lib")
        #endif
    #endif
#endif
```

Plikach nagłówkowych MFC również zawierać dyrektywy łącze w wszystkie wymagane biblioteki, łącznie z biblioteki MFC, bibliotek Win32, bibliotek OLE, bibliotek OLE, utworzony na podstawie próbki, biblioteki ODBC i tak dalej.

## <a name="ansi-mbcs-and-unicode"></a>ANSI, MBCS i Unicode

Wersje biblioteki MFC ANSI/MBCS obsługuje oba zestawy znaków jednobajtowych, takich jak ASCII i znaków wielobajtowych ustawia takie jak Shift-JIS. Wersje biblioteki MFC Unicode obsługują znaki Unicode w postaci UTF-16LE zakodowanych znaków dwubajtowych. Dla obsługi standardu Unicode kodowany w formacie UTF-8, należy użyć ANSI/MBCS wersji biblioteki MFC.

Aby ustawić konfigurację projektu tak, aby korzystać z jednobajtowych wielobajtowych i szerokich znaków Unicode ciągów i pomocy technicznej w IDE, użyj **właściwości projektu** okna dialogowego. W **właściwości konfiguracji** > **ogólne** ustaw **zestaw znaków** właściwości **Nieustawione** do użycia zestaw znaków jednobajtowych. Ustaw właściwość **Użyj zestawu znaków wielobajtowych** do korzystania z zestawu znaków wielobajtowych lub **Użyj zestawu znaków Unicode** używać zakodowanymi w formacie UTF-16 Unicode.

Projekty MFC korzystają symbol preprocesora \_UNICODE, aby wskazać, UTF-16 znaków dwubajtowych obsługi standardu Unicode, i \_Obsługa MBCS w celu wskazania MBCS. Te opcje są wzajemnie wykluczających się w projekcie.

## <a name="mfc-static-library-naming-conventions"></a>Konwencje nazewnictwa MFC biblioteki statycznej

Biblioteki statyczne dla MFC, użyj następujących konwencji nazewnictwa. Nazwy bibliotek mają następującą formę

> <em>u</em>AFX<em>cd</em>. LIB

gdzie litery kursywą małe litery są symbolami zastępczymi Specyfikatory, których znaczenie są wyświetlane w poniższej tabeli:

|Specyfikator|Wartości i znaczenia|
|---------------|-------------------------|
|*u*|ANSI/MBCS (N) lub Unicode (U); Pomiń wersji bez formantów MFC w oknach dialogowych|
|*c*|Wersja kontrolki MFC w oknach dialogowych (efektywna) lub bez (NMCD)|
|*d*|Debuguj lub Uwolnij: D = debugowania; Pominięto specyfikator wersji|

Wszystkie biblioteki, wymienione w poniższej tabeli uwzględniono wbudowanych w bieżącym katalogu \atlmfc\lib dla architektur obsługiwanej kompilacji.

|Biblioteka|Opis|
|-------------|-----------------|
|NAFXCW.LIB|Biblioteka dołączana statycznie MFC, wersji|
|NAFXCWD.LIB|Biblioteka dołączana statycznie MFC, wersja do debugowania|
|UAFXCW.LIB|Biblioteka dołączana statycznie MFC z obsługą standardu Unicode i wersji|
|UAFXCWD.LIB|Biblioteka dołączana statycznie MFC z obsługą standardu Unicode, wersja do debugowania|
|AFXNMCD.LIB|Biblioteka dołączana statycznie MFC bez kontrolki okna dialogowego MFC, wersji|
|AFXNMCDD.LIB|Biblioteka dołączana statycznie MFC bez kontrolki okna dialogowego MFC, wersja do debugowania|

Pliki debugera, które mają taką samą nazwę bazy i rozszerzenia .pdb są również dostępne dla wszystkich bibliotek statycznych.

## <a name="mfc-shared-dll-naming-conventions"></a>Konwencje nazewnictwa bibliotek DLL współdzielone MFC

Współdzielone MFC DLL również wykonaj ustrukturyzowaną konwencję nazewnictwa. Ta funkcja ułatwia wiedzieć, które biblioteki DLL lub biblioteki powinien być używany dla wybranych celów.

Biblioteki MFC DLL ma *wersji* numery, które wskazują zgodność binarną. Za pomocą biblioteki MFC dll, który ma tę samą wersję, jak inne biblioteki i zestaw narzędzi kompilatora, aby zagwarantować zgodność w ramach projektu.

|DLL|Opis|
|---------|-----------------|
|MFC*wersji*. BIBLIOTEKI DLL|Wersji biblioteki MFC DLL, ANSI lub MBCS wersji|
|MFC*wersji*U.DLL|Biblioteki MFC DLL wersji standardu Unicode|
|MFC*wersji*D.DLL|Wersji biblioteki MFC DLL, ANSI lub debugować MBCS|
|MFC*wersji*UD. BIBLIOTEKI DLL|Biblioteki MFC DLL, wersja do debugowania kodu Unicode|
|MFCM*wersji*. BIBLIOTEKI DLL|Biblioteki MFC DLL za pomocą kontrolek Windows Forms, wersji ANSI lub MBCS wersji|
|MFCM*wersji*U.DLL|Biblioteki MFC DLL za pomocą kontrolek Windows Forms, wersja Unicode|
|MFCM*wersji*D.DLL|Biblioteki MFC DLL za pomocą kontrolek Windows Forms, wersji ANSI lub debugować MBCS|
|MFCM*wersji*UD. BIBLIOTEKI DLL|Biblioteki MFC DLL za pomocą kontrolek Windows Forms, wersja do debugowania kodu Unicode|

Bibliotek importu potrzebne do tworzenia aplikacji lub biblioteki dll, korzystających z tych udostępnionych bibliotek DLL rozszerzeń MFC mają taką samą nazwę bazy jak biblioteka DLL, ale mają rozszerzenie nazwy pliku .lib. Korzystając z udostępnionych bibliotek DLL, mały biblioteki statycznej nadal muszą być połączone z kodem; Ta biblioteka ma nazwę MFCS*wersji*.lib {N} {D}.

Możesz dynamicznie łączenia z udostępnionych wersji biblioteki DLL MFC, czy jest ono z aplikacji lub z biblioteki DLL rozszerzenia MFC, musi zawierać dopasowania MFC*wersji*. Biblioteki DLL lub MFC*wersji*U.DLL po wdrożeniu swojego produktu.

Aby uzyskać listę bibliotek DLL Visual C++, które mogą być dystrybuowane za pomocą aplikacji, zobacz [Kod dystrybucyjny dla programu Microsoft Visual Studio 2017 i Microsoft Visual Studio 2017 SDK (obejmuje programy narzędziowe i pliki BuildServer)](http://go.microsoft.com/fwlink/p/?LinkId=823098).

Aby uzyskać więcej informacji na temat obsługi MBCS i Unicode w MFC, zobacz [Obsługa zestawu znaków wielobajtowych (MBCS) i Unicode](../atl-mfc-shared/unicode-and-multibyte-character-set-mbcs-support.md).

## <a name="dynamic-link-library-support"></a>Obsługa bibliotek dołączanych dynamicznie

Można użyć albo statycznych lub współdzielonej dynamicznych bibliotek MFC do tworzenia bibliotek DLL, które mogą być używane przez pliki wykonywalne MFC i innego typu niż MFC. Są to tak zwane "regularne biblioteki dll" lub "zwykłych bibliotekach MFC dll", aby odróżnić je od rozszerzenia MFC biblioteki dll, które mogą być tylko używane przez aplikacje MFC i MFC DLL. Skompilowanych przy użyciu statycznej biblioteki MFC DLL jest czasami nazywane USRDLL w starszych odwołań, ponieważ projekty biblioteki MFC DLL, zdefiniuj symbol preprocesora  **\_USRDLL**. Biblioteki DLL używającego MFC udostępnionych bibliotek DLL jest czasami nazywane AFXDLL w starszych odwołań, ponieważ definiuje symbol preprocesora  **\_AFXDLL**.

Po utworzeniu projektu biblioteki DLL, łącząc w bibliotekach statycznych MFC DLL można wdrożyć bez MFC współdzielonych bibliotek DLL. Gdy projektu biblioteki DLL łączy się z bibliotekami importowanymi MFC*wersji*. LIB lub MFC*wersji*U.LIB, należy wdrożyć dopasowywania współdzielone MFC DLL MFC*wersji*. Biblioteki DLL lub MFC*wersji*U.DLL wraz z biblioteką DLL. Aby uzyskać więcej informacji, zobacz [biblioteki dll](../build/dlls-in-visual-cpp.md).

## <a name="see-also"></a>Zobacz także

[Tematy ogólne dotyczące MFC](../mfc/general-mfc-topics.md)
