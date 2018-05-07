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
ms.openlocfilehash: 9fb4f73d1a0360ddad3983179415d0f7fc2d3cda
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="mfc-library-versions"></a>Wersje biblioteki MFC

Biblioteki MFC jest dostępna w wersjach, które obsługują jednobajtowe ANSI i ustawić znaków wielobajtowych (MBCS) kodu, a także wersje, które obsługują standardu Unicode (zakodowane jako UTF-16LE, zestaw znaków macierzystego systemu Windows). Każda wersja MFC jest dostępna jako bibliotekę statyczną lub współdzielonej bibliotece DLL. Istnieje również mniejsze wersji biblioteki statycznej MFC, który powoduje, że formantów MFC w oknach dialogowych dla aplikacji, które są bardzo wrażliwe na wielkość i nie wymagają tych kontrolek. Biblioteki MFC są dostępne w obu debugowania i wydania wersji dla obsługiwane architektury, które obejmują x86, x64 i procesorów ARM. Możesz utworzyć obie aplikacje (pliki .exe) i bibliotek DLL z dowolnej wersji biblioteki MFC. Istnieje również zestawu skompilowanego dla powiązania z kodu zarządzanego biblioteki MFC. Biblioteki DLL udostępnionych MFC obejmują numer wersji, aby wskazać zgodności plików binarnych biblioteki.

## <a name="automatic-linking-of-mfc-library-versions"></a>Automatyczne łączenie wersji biblioteki MFC

Pliki nagłówka MFC automatycznie określić poprawną wersję biblioteki MFC, aby połączyć, na podstawie wartości zdefiniowane w danym środowisku kompilacji. Pliki nagłówka MFC Dodaj dyrektywy kompilatora poinstruowanie konsolidator łącze w określonej wersji biblioteki MFC.

Na przykład AFX. Plik nagłówka H informuje konsolidator, aby łącze w pełnej statycznych, ograniczone statyczny lub wspólny wersja biblioteki DLL MFC; ANSI/MBCS lub Unicode wersji; i debugowania lub wersji detalicznej wersji, w zależności od konfiguracji kompilacji:

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

Pliki nagłówkowe MFC również zawiera dyrektywy, które mają być połączone wszystkie wymagane biblioteki, włączając biblioteki MFC, biblioteki Win32, bibliotek OLE, bibliotek OLE zbudowane na podstawie próbek, biblioteki ODBC i tak dalej. 

## <a name="ansi-mbcs-and-unicode"></a>ANSI, MBCS i Unicode

Wersje biblioteki MFC ANSI/MBCS obsługuje oba zestawy znaków, takich jak ASCII i zestawy znaków wielobajtowych, takie jak Shift JIS. Wersje biblioteki MFC Unicode obsługują standardu Unicode w formie zakodowanej jego UTF-16LE znaków dwubajtowych. ANSI/MBCS wersje biblioteki MFC należy użyć do obsługi formatu Unicode kodowany w formacie UTF-8.

Aby ustawić konfigurację projektu do użycia w środowisku IDE jednobajtowe wielobajtowe i znaków dwubajtowych obsługi formatu Unicode ciągów i znakowe, użyj **właściwości projektu** okna dialogowego. W **właściwości konfiguracji** > **ogólne** ustaw **zestaw znaków** właściwości **Nieustawione** do użycia zestaw znaków jednobajtowych. Ustaw dla właściwości **Użyj wielobajtowy zestaw znaków,** korzystanie ze zestawu znaków wielobajtowych lub **użyć zestawu znaków Unicode** do użycia Unicode został zakodowany jako UTF-16.

Projekty MFC Użyj symbol preprocesora  **\_UNICODE** wskazująca UTF-16 znaków dwubajtowych obsługi formatu Unicode, i  **\_MBCS** wskazująca MBCS pomocy technicznej. Te opcje są wzajemnie w projekcie.

## <a name="mfc-static-library-naming-conventions"></a>Konwencje nazewnictwa biblioteką statyczną MFC

Biblioteki statyczne dla MFC Użyj następujących konwencji nazewnictwa. Nazwy bibliotek mają następującą postać

> *u*AFX*c**d*.LIB

gdzie kursywą małe litery są symbole zastępcze Specyfikatory, których znaczenie przedstawiono w poniższej tabeli:

|Specyfikator|Wartości i znaczenia|
|---------------|-------------------------|
|*u*|ANSI/MBCS (N) lub Unicode (U); Pomiń dla wersji bez formantów MFC w oknach dialogowych|
|*c*|Wersja z formantów MFC w oknach dialogowych (efektywna) lub bez (NMCD)|
|*d*|Debugowania i wydania: D = Debug; Pomiń specyfikator wersji|

Uwzględniane są wszystkie biblioteki, wymienione w poniższej tabeli wbudowane w katalogu \atlmfc\lib architektur obsługiwanych kompilacji.

|Biblioteka|Opis|
|-------------|-----------------|
|NAFXCW.LIB|Biblioteka dołączana statycznie MFC, wersja|
|NAFXCWD.LIB|Biblioteka dołączana statycznie MFC, wersja do debugowania|
|UAFXCW.LIB|Biblioteka dołączana statycznie MFC z obsługą Unicode, wersja|
|UAFXCWD.LIB|Biblioteka dołączana statycznie MFC z obsługą Unicode, wersja do debugowania|
|AFXNMCD.LIB|Biblioteka dołączana statycznie MFC bez kontrolki okna dialogowego MFC, wersja|
|AFXNMCDD.LIB|Biblioteka dołączana statycznie MFC bez kontrolki okna dialogowego MFC, wersja do debugowania|

Pliki debugera, które mają taką samą nazwę podstawową i rozszerzenia .pdb są również dostępne dla poszczególnych bibliotek statycznych.

## <a name="mfc-shared-dll-naming-conventions"></a>Konwencje nazewnictwa bibliotek DLL udostępnionych MFC

MFC udostępnione biblioteki DLL również wykonaj strukturalnych konwencji nazewnictwa. Ułatwia ustalenie, które biblioteki DLL lub biblioteki powinien być używany w celu, które.

Biblioteki DLL MFC ma *wersji* numery, które wskazuje zgodności plików binarnych. Za pomocą biblioteki DLL MFC mające tej samej wersji, co inne biblioteki i zestawu narzędzi kompilatora, aby zagwarantować zgodności w projekcie.

|DLL|Opis|
|---------|-----------------|
|MFC*wersji*. BIBLIOTEKI DLL|Wersja biblioteki DLL MFC, ANSI lub wersji MBCS|
|MFC*wersji*U.DLL|Biblioteki MFC DLL wersji Unicode|
|MFC*wersji*D.DLL|Wersja biblioteki DLL MFC, ANSI lub debugowania MBCS|
|MFC*wersji*UD. BIBLIOTEKI DLL|Biblioteki MFC DLL wersji do debugowania kodu Unicode|
|MFCM*wersji*. BIBLIOTEKI DLL|Biblioteki MFC DLL z formanty formularzy systemu Windows, wersja ANSI lub wersji MBCS|
|MFCM*wersji*U.DLL|Biblioteki MFC DLL z formanty formularzy systemu Windows, wersja wydana Unicode|
|MFCM*wersji*D.DLL|Biblioteki MFC DLL z formanty formularzy systemu Windows, wersja ANSI lub debugowania MBCS|
|MFCM*wersji*UD. BIBLIOTEKI DLL|Biblioteki MFC DLL z formanty formularzy systemu Windows, wersja do debugowania kodu Unicode|

Biblioteki importu niezbędnych do tworzenia aplikacji lub biblioteki dll, korzystających z tych udostępnionej biblioteki DLL rozszerzeń MFC ma taką samą nazwę podstawową jak plik DLL, ale ma rozszerzenie nazwy pliku lib. Korzystając z udostępnionej biblioteki dll, mała biblioteki statycznej nadal musi być połączony z kodu; Ta biblioteka ma nazwę MFCS*wersji*.lib {U} {D}.

Możesz dynamicznie łączenia z udostępnionego wersja biblioteki DLL MFC, czy z aplikacji lub z biblioteki DLL rozszerzenia MFC, musi zawierać dopasowania MFC*wersji*. Biblioteki DLL lub MFC*wersji*U.DLL podczas wdrażania pakietu.

Aby uzyskać listę Visual dll C++, które mogą być dystrybuowane za pomocą aplikacji, zobacz [Kod dystrybucyjny dla programu Microsoft Visual Studio 2017 i Microsoft Visual Studio 2017 SDK (obejmuje narzędzia i pliki BuildServer)](http://go.microsoft.com/fwlink/p/?LinkId=823098).

Aby uzyskać więcej informacji na temat obsługi MBCS i Unicode w MFC, zobacz [Unicode i pomocy technicznej ustawić znaków wielobajtowych (MBCS)](../atl-mfc-shared/unicode-and-multibyte-character-set-mbcs-support.md).

## <a name="dynamic-link-library-support"></a>Obsługa bibliotek dołączanych dynamicznie

Albo statyczny lub wspólny dynamicznej biblioteki MFC służy do tworzenia bibliotek DLL, które mogą być używane przez pliki wykonywalne zarówno MFC, jak i innego typu niż MFC. Są one nazywane "dll" lub "regularne biblioteki DLL MFC", aby odróżnić je od rozszerzeń MFC dll, które mogą być tylko używane przez aplikacje MFC i MFC DLL. Skompilowane przy użyciu bibliotek statycznych MFC DLL jest czasem nazywany USRDLL w starszych odwołań, ponieważ projekty MFC DLL Określa symbol preprocesora  **\_USRDLL**. Biblioteki DLL używającego MFC DLL udostępnionych jest czasem nazywany AFXDLL w starszych odwołań, ponieważ Określa symbol preprocesora  **\_AFXDLL**.

Po utworzeniu projektu biblioteki DLL przez połączenie w bibliotekach statycznych MFC biblioteki DLL można wdrożyć bez MFC udostępnione biblioteki dll. Gdy projektu biblioteki DLL łączy się z bibliotekami importowanymi MFC*wersji*. LIB lub MFC*wersji*U.LIB, należy wdrożyć dopasowywania MFC udostępnionych DLL MFC*wersji*. Biblioteki DLL lub MFC*wersji*U.DLL wraz z biblioteki DLL. Aby uzyskać więcej informacji, zobacz [biblioteki dll](../build/dlls-in-visual-cpp.md).

## <a name="see-also"></a>Zobacz także

[Tematy ogólne dotyczące MFC](../mfc/general-mfc-topics.md)  
