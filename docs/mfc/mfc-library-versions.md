---
title: Wersje biblioteki MFC
ms.date: 05/08/2019
helpviewer_keywords:
- class libraries [MFC], building versions
- version information [MFC], MFC library
- MFC class library
- MFC class library, building
- MFC libraries
- MFC, library versions
- libraries [MFC], versions
ms.openlocfilehash: b8e32366d9ff43bd6e5770f64f0ba9d8bf6e56ab
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2020
ms.locfileid: "78856803"
---
# <a name="mfc-library-versions"></a>Wersje biblioteki MFC

Biblioteka MFC jest dostępna w wersjach, które obsługują kod ANSI jednobajtowych i zestaw znaków MBCS, a także wersje obsługujące kodowanie Unicode (kodowane jako UTF-16LE, zestaw znaków natywnych systemu Windows). Każda wersja MFC jest dostępna jako Biblioteka statyczna lub jako udostępniona biblioteka DLL. Istnieje również mniejsza wersja biblioteki statycznej MFC, która pozostawia Formanty MFC dla okien dialogowych, dla aplikacji, które są bardzo wrażliwe na rozmiar i nie potrzebują tych kontrolek. Biblioteki MFC są dostępne zarówno w wersji Debug, jak i wydań dla obsługiwanych architektur, które obejmują procesory x86, x64 i ARM. Można tworzyć zarówno aplikacje (pliki. exe), jak i biblioteki DLL, przy użyciu dowolnej wersji biblioteki MFC. Istnieje również zestaw bibliotek MFC skompilowanych pod kątem współdziałania z kodem zarządzanym. Udostępnione biblioteki DLL MFC zawierają numer wersji, aby wskazać zgodność biblioteki binarnej.

## <a name="automatic-linking-of-mfc-library-versions"></a>Automatyczne łączenie wersji biblioteki MFC

Pliki nagłówkowe MFC automatycznie określają poprawną wersję biblioteki MFC do konsolidacji na podstawie wartości zdefiniowanych w środowisku kompilacji. Pliki nagłówkowe MFC dodają dyrektywy kompilatora, które nakazuje konsolidatorowi łączenie się z określoną wersją biblioteki MFC.

Na przykład AFX. Plik nagłówkowy H nakazuje konsolidatorowi łączenie w pełnej statycznej, ograniczonej statycznej lub udostępnionej wersji biblioteki DLL MFC; Wersja ANSI/MBCS lub Unicode; i wersje Debug lub handlowe, w zależności od konfiguracji kompilacji:

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

Pliki nagłówkowe MFC obejmują również dyrektywy do łączenia we wszystkich wymaganych bibliotekach, w tym biblioteki MFC, biblioteki Win32, biblioteki OLE, biblioteki OLE utworzone na podstawie przykładów, bibliotek ODBC i tak dalej.

## <a name="ansi-mbcs-and-unicode"></a>ANSI, MBCS i Unicode

Wersje biblioteki MFC ANSI/MBCS obsługują zarówno jednobajtowe zestawy znaków, jak ASCII, jak i zestawy znaków wielowymiarowych, takie jak Shift-JIS. Wersje biblioteki Unicode MFC obsługują standard Unicode w postaci kodowanej jednobajtowej postaci UTF-16LE. Użyj bibliotek MFC/MBCS w wersji Library w przypadku obsługi kodowania Unicode w formacie UTF-8.

Aby skonfigurować konfigurację projektu w taki sposób, aby w środowisku IDE był używany ciąg Unicode jednobajtowy, wielobajtowy lub szeroki znak oraz obsługa znaków, użyj okna dialogowego **właściwości projektu** . Na stronie **Ogólne** **Właściwości konfiguracji** > ustaw właściwość **zestaw znaków** , aby nie była **ustawiona** na używanie jednobajtowego zestawu znaków. Ustaw właściwość w taki sposób, aby korzystała z zestawu znaków **wielobajtowych** do użycia zestawu znaków wielobajtowych, lub **Użyj zestawu znaków Unicode** , aby używać kodowania Unicode jako UTF-16.

Projekty MFC używają symboli preprocesora \_UNICODE, aby wskazać obsługę Unicode w formacie UTF-16, a \_MBCS, aby wskazać obsługę MBCS. Te opcje wzajemnie się wykluczają w projekcie.

## <a name="mfc-static-library-naming-conventions"></a>Konwencje nazewnictwa bibliotek statycznych MFC

Biblioteki statyczne dla MFC używają następujących konwencji nazewnictwa. Nazwy bibliotek mają postać

> <em>u</em> AFX<em>CD</em>. LIB

gdzie litery wyświetlane w kursywie są symbolami zastępczymi dla specyfikatorów, których znaczenie jest pokazane w poniższej tabeli:

|Specyfikator|Wartości i znaczenie|
|---------------|-------------------------|
|*'t*|ANSI/MBCS (N) lub Unicode (U); Pomiń w przypadku wersji bez formantów MFC w oknach dialogowych|
|*s*|Wersja z kontrolkami MFC w oknach dialogowych (CW) lub bez (NMCD)|
|*Wykres*|Debugowanie lub wydanie: D = debugowanie; Pomiń specyfikator dla wydania|

Wszystkie biblioteki wymienione w poniższej tabeli są dołączone do katalogu \atlmfc\lib dla obsługiwanych architektur kompilacji.

|Biblioteka|Opis|
|-------------|-----------------|
|NAFXCW.LIB|Biblioteka DLL biblioteki MFC, wersja wydania|
|NAFXCWD.LIB|Biblioteka DLL biblioteki MFC, wersja do debugowania|
|UAFXCW.LIB|Biblioteka DLL biblioteki MFC z obsługą standardu Unicode, wersja wydania|
|UAFXCWD.LIB|Biblioteka DLL biblioteki MFC z obsługą standardu Unicode, wersja do debugowania|
|AFXNMCD.LIB|Biblioteka DLL biblioteki MFC bez kontrolek okna dialogowego MFC, wersja wydania|
|AFXNMCDD.LIB|Biblioteka DLL biblioteki MFC bez kontrolek okna dialogowego MFC, wersja do debugowania|

Pliki debugera mające taką samą nazwę podstawową i rozszerzenie. pdb są również dostępne dla każdej biblioteki statycznej.

## <a name="mfc-shared-dll-naming-conventions"></a>Konwencje nazewnictwa udostępnionych bibliotek DLL MFC

Udostępnione biblioteki DLL MFC są również zgodne z konwencją nazewnictwa strukturalnego. Dzięki temu można łatwiej wiedzieć, która Biblioteka DLL lub biblioteka powinna być używana do tego celu.

Biblioteki MFC DLL mają numery *wersji* wskazujące zgodność binarną. Użyj bibliotek MFC DLL, które mają taką samą wersję jak inne biblioteki i zestaw narzędzi kompilatora, aby zagwarantować zgodność w ramach projektu.

|DLL|Opis|
|---------|-----------------|
|*Wersja*MFC. BIBLIOTECE|Biblioteka MFC DLL, wersja ANSI lub MBCS|
|Biblioteka MFC w*wersji*U. dll|MFC DLL, wersja w wersji Unicode|
|MFC*wersja*D. dll|Wersja debugowania biblioteki MFC DLL, ANSI lub MBCS|
|*Wersja*MFC ud. BIBLIOTECE|MFC DLL, wersja debugowania Unicode|
|*Wersja*MFCM. BIBLIOTECE|Biblioteka MFC DLL z kontrolkami Windows Forms, wersjami ANSI lub MBCS|
|MFCM*wersja*U. dll|Biblioteka MFC DLL z kontrolkami Windows Forms, wersja Unicode|
|MFCM*wersja*D. dll|Biblioteka MFC DLL z kontrolkami Windows Forms, wersja debugowania ANSI lub MBCS|
|MFCM*wersja*ud. BIBLIOTECE|Biblioteka MFC DLL z kontrolkami Windows Forms, wersja Debug Unicode|

Biblioteki importowe, które są konieczne do kompilowania aplikacji lub bibliotek DLL rozszerzeń MFC korzystających z tych udostępnionych bibliotek DLL, mają taką samą nazwę bazową jak biblioteka DLL, ale mają rozszerzenie nazwy pliku. lib. W przypadku korzystania z udostępnionych bibliotek DLL niewielka biblioteka statyczna musi być nadal połączona z kodem; Ta biblioteka ma nazwę MFCS w*wersji*{U} {D}. lib.

W przypadku dynamicznego łączenia z udostępnioną biblioteką DLL MFC, niezależnie od tego, czy pochodzi ona z aplikacji, czy z biblioteki DLL rozszerzenia MFC, należy dołączyć zgodną*wersję*MFC. DLL lub MFC w*wersji*U. dll podczas wdrażania produktu.

Aby zapoznać się z listą wizualnych C++ bibliotek DLL, które mogą być dystrybuowane z aplikacjami, zobacz [Kod dystrybucyjny dla Microsoft Visual Studio 2017 i Microsoft Visual Studio 2017 SDK (zawiera narzędzia i pliki BuildServer)](/visualstudio/productinfo/2017-redistribution-vs) lub [Kod dystrybucyjny dla programu Visual Studio 2019](/visualstudio/releases/2019/redistribution).

Aby uzyskać więcej informacji na temat obsługi MBCS i Unicode w MFC, zobacz [Obsługa zestawów znaków Unicode i wielobajtowych (MBCS)](../atl-mfc-shared/unicode-and-multibyte-character-set-mbcs-support.md).

## <a name="dynamic-link-library-support"></a>Obsługa bibliotek dołączanych dynamicznie

Możesz użyć statycznej lub udostępnionej dynamicznie biblioteki MFC do tworzenia bibliotek DLL, które mogą być używane przez pliki wykonywalne MFC i inne niż MFC. Są one nazywane "regularnymi bibliotekami DLL" lub "regularnymi bibliotekami MFC dll", aby odróżnić je od bibliotek DLL rozszerzeń MFC, które mogą być używane tylko przez aplikacje MFC i biblioteki DLL MFC. Biblioteka DLL skompilowana przy użyciu bibliotek statycznych MFC jest czasami nazywana USRDLL w starszych odwołaniach, ponieważ projekty DLL MFC definiują symbol preprocesora **\_USRDLL**. Biblioteka DLL, która używa udostępnionych bibliotek DLL MFC, jest czasami nazywana AFXDLL w starszych odwołaniach, ponieważ definiuje symbol preprocesora **\_AFXDLL**.

Podczas tworzenia projektu DLL przez połączenie z bibliotekami statycznymi MFC Biblioteka DLL może zostać wdrożona bez udostępnionych bibliotek DLL MFC. Gdy projekt DLL łączy się z*wersją*MFC bibliotek importu. LIB lub MFC*wersja*U. lib, należy wdrożyć zgodną*wersję*MFC udostępnionej biblioteki MFC. DLL lub MFC*wersja*U. dll wraz z biblioteką DLL. Aby uzyskać więcej informacji, zobacz [biblioteki DLL](../build/dlls-in-visual-cpp.md).

## <a name="see-also"></a>Zobacz także

[Tematy ogólne dotyczące MFC](../mfc/general-mfc-topics.md)
