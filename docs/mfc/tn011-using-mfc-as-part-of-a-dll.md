---
title: 'TN011: używanie MFC jako części biblioteki DLL'
ms.date: 11/04/2016
helpviewer_keywords:
- _USRDLL symbol
- USRDLLs, compiler switches
- TN011
- DLLs [MFC], linking
- MFC DLLs [MFC], linking regular MFC DLLs to MFC
ms.assetid: 76753e9c-59dc-40f6-b6a7-f6bb9a7c4190
ms.openlocfilehash: 0f4d4e2ed76a0fa5f8f775345fc672a1df055a39
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370436"
---
# <a name="tn011-using-mfc-as-part-of-a-dll"></a>TN011: używanie MFC jako części biblioteki DLL

W tej notatce opisano zwykłe biblioteki DLL MFC, które umożliwiają korzystanie z biblioteki MFC jako części biblioteki dynamicznego łącza systemu Windows (DLL). Zakłada się, że jesteś zaznajomiony z bibliotekami DLL systemu Windows i jak je tworzyć. Aby uzyskać informacje na temat bibliotek DLL rozszerzeń MFC, za pomocą których można tworzyć rozszerzenia do biblioteki MFC, zobacz [Wersja bibliotekI DLL MFC](../mfc/tn033-dll-version-of-mfc.md).

## <a name="dll-interfaces"></a>Interfejsy DLL

regularne biblioteki DLL MFC zakładają, że interfejsy między aplikacją a biblioteką DLL są określone w funkcjach c-like lub jawnie eksportowane klasy. Nie można wyeksportować interfejsów klasy MFC.

Jeśli zarówno biblioteki DLL i aplikacji chcesz użyć MFC, oba mają możliwość korzystania z udostępnionej wersji bibliotek MFC lub statycznie łącze do kopii bibliotek. Aplikacja i biblioteka DLL mogą używać jednej ze standardowych wersji biblioteki MFC.

regularne biblioteki DLL MFC mają kilka zalet:

- Aplikacja, która używa biblioteki DLL nie musi używać MFC i nie musi być aplikacją Visual C++.

- W przypadku zwykłych bibliotek DLL MFC, które statycznie łączą się z MFC, rozmiar biblioteki DLL zależy tylko od procedur wykonywania MFC i C, które są używane i połączone.

- W przypadku zwykłych bibliotek DLL MFC, które dynamicznie łączą się z MFC, oszczędności w pamięci wynikające z używania udostępnionej wersji MFC mogą być znaczące. Jednak należy rozpowszechniać udostępnione\<biblioteki DLL,*wersja* Mfc>.dll i\<*wersja* Msvvcrt>.dll, z biblioteką DLL.

- Projekt biblioteki DLL jest niezależna od sposobu implementowania klas. Projekt biblioteki DLL eksportuje tylko do żądanych interfejsów API. W rezultacie, jeśli implementacja ulegnie zmianie, regularne biblioteki DLL MFC są nadal ważne.

- Z regularnych bibliotek DLL MFC, które statycznie łączą się z MFC, jeśli zarówno biblioteki DLL i aplikacji mfc, nie ma żadnych problemów z aplikacją, która chce innej wersji MFC niż biblioteki DLL lub odwrotnie. Ponieważ biblioteka MFC jest statycznie połączone do każdej biblioteki DLL lub EXE, nie ma wątpliwości, która wersja masz.

## <a name="api-limitations"></a>Ograniczenia API

Niektóre funkcje MFC nie ma zastosowania do wersji DLL, albo z powodu ograniczeń technicznych lub ponieważ te usługi są zwykle dostarczane przez aplikację. W przypadku bieżącej wersji MFC jedyną funkcją, która nie ma zastosowania, jest `CWinApp::SetDialogBkColor`.

## <a name="building-your-dll"></a>Tworzenie biblioteki DLL

Podczas kompilowania regularnych bibliotek DLL MFC, które statycznie łączą się z MFC, symbole `_USRDLL` i `_WINDLL` muszą być zdefiniowane. Kod biblioteki DLL musi być również skompilowany z następującymi przełącznikami kompilatora:

- **/D_WINDLL** oznacza, że kompilacja jest dla biblioteki DLL

- **/D_USRDLL** określa, że budujesz zwykłą bibliotekę DLL MFC

Należy również zdefiniować te symbole i używać tych przełączników kompilatora podczas kompilowania regularnych bibliotek DLL MFC, które dynamicznie łączą się z MFC. Ponadto symbol `_AFXDLL` musi być zdefiniowany, a kod biblioteki DLL musi być skompilowany z:

- **/D_AFXDLL** określa, że budujesz zwykłą bibliotekę DLL MFC, która dynamicznie łączy się z MFC

Interfejsy (API) między aplikacją a biblioteką DLL muszą być jawnie eksportowane. Zaleca się zdefiniowanie interfejsów jako niskiej przepustowości i używanie tylko interfejsów C, jeśli to możliwe. Bezpośrednie interfejsy C są łatwiejsze do utrzymania niż bardziej złożone klasy C++.

Umieść interfejsy API w osobnym nagłówku, który może być dołączony zarówno przez pliki C, jak i C++. Zobacz screencap.h nagłówka w przykładzie MFC Advanced Concepts [DLLScreenCap](../overview/visual-cpp-samples.md) na przykład. Aby wyeksportować funkcje, wprowadź je w `EXPORTS` sekcji pliku definicji modułu (. DEF) lub `__declspec(dllexport)` uwzględnić w definicjach funkcji. Służy `__declspec(dllimport)` do importowania tych funkcji do pliku wykonywalnego klienta.

Na początku wszystkich eksportowanych funkcji w zwykłych bibliotekach DLL MFC, które dynamicznie łączą się z bibliotekami MFC, należy dodać makro AFX_MANAGE_STATE na początku wszystkich eksportowanych funkcji w zwykłych bibliotekach DLL MFC, które dynamicznie łączą się z mfc. To makro ustawia bieżący stan modułu na ten dla biblioteki DLL. Aby użyć tego makra, dodaj następujący wiersz kodu na początku funkcji eksportowanych z biblioteki DLL:

`AFX_MANAGE_STATE(AfxGetStaticModuleState( ))`

## <a name="winmain---dllmain"></a>WinMain -> DllMain

Biblioteka MFC definiuje standardowy `DllMain` punkt wejścia Win32, który inicjuje obiekt pochodny [CWinApp,](../mfc/reference/cwinapp-class.md) jak w typowej aplikacji MFC. Umieść wszystkie inicjalizacji specyficzne dla biblioteki DLL w [InitInstance](../mfc/reference/cwinapp-class.md#initinstance) metody, jak w typowej aplikacji MFC.

Należy zauważyć, że [mechanizm CWinApp::Run](../mfc/reference/cwinapp-class.md#run) nie ma zastosowania do biblioteki DLL, ponieważ aplikacja jest właścicielem pompy wiadomości głównej. Jeśli biblioteka DLL wyświetla niemodowe okna dialogowe lub ma własne okno ramki głównej, główna pompa wiadomości aplikacji musi wywołać procedurę eksportowane przez bibliotekę DLL, która wywołuje [CWinApp::PreTranslateMessage](../mfc/reference/cwinapp-class.md#pretranslatemessage).

Zobacz przykład DLLScreenCap do korzystania z tej funkcji.

Funkcja, `DllMain` która zapewnia MFC wywoła [CWinApp::ExitInstance](../mfc/reference/cwinapp-class.md#exitinstance) metody klasy, `CWinApp` która pochodzi z przed DLL jest zwalniany.

## <a name="linking-your-dll"></a>Łączenie biblioteki DLL

W regularnych bibliotekach DLL MFC, które statycznie łączą się z MFC, należy połączyć bibliotekę DLL z nafxcwd.lib lub Nafxcw.lib i z wersją środowiska wykonawczego C o nazwie Libcmt.lib. Biblioteki te są wstępnie utworzone i mogą być instalowane przez określenie ich podczas uruchamiania konfiguracji języka Visual C++.

## <a name="sample-code"></a>Przykładowy kod

Zobacz przykładowy program MFC Advanced Concepts DLLScreenCap, aby uzyskać pełną próbkę. Kilka ciekawych rzeczy, na które należy zwrócić uwagę w tym przykładzie, jest następujących:

- Flagi kompilatora biblioteki DLL i tych aplikacji są różne.

- Linie łączy i . Pliki DEF dla biblioteki DLL i te dla aplikacji są różne.

- Aplikacja, która używa biblioteki DLL nie musi być w języku C++.

- Interfejs między aplikacją a biblioteką DLL jest interfejsem API, który jest użyteczny przez C lub C++ i jest eksportowany za pomocą pliku DLLScreenCap.def.

Poniższy przykład ilustruje interfejs API, który jest zdefiniowany w regularnych biblioteki DLL MFC, która statycznie łączy się z MFC. W tym przykładzie deklaracja jest `extern "C" { }` ujęta w bloku dla użytkowników języka C++. Ma to kilka zalet. Po pierwsze sprawia, że interfejsy API biblioteki DLL można egoużyć za pomocą aplikacji klienckich innych niż C++. Po drugie zmniejsza obciążenie biblioteki DLL, ponieważ nazwa języka C++ nie zostanie zastosowana do wyeksportowaną nazwy. Wreszcie, ułatwia jawne dodawanie do . DEF (do eksportowania przez porządki) bez konieczności martwienia się o mangling nazwy.

```cpp
#ifdef __cplusplus
extern "C" {
#endif  /* __cplusplus */

struct TracerData
{
    BOOL bEnabled;
    UINT flags;
};

BOOL PromptTraceFlags(TracerData FAR* lpData);

#ifdef __cplusplus
}
#endif
```

Struktury używane przez interfejs API nie są pochodną klas MFC i są zdefiniowane w nagłówku interfejsu API. Zmniejsza to złożoność interfejsu między biblioteką DLL a aplikacją i sprawia, że biblioteka DLL jest użyteczna przez programy C.

## <a name="see-also"></a>Zobacz też

[Uwagi techniczne według numerów](../mfc/technical-notes-by-number.md)<br/>
[Uwagi techniczne według kategorii](../mfc/technical-notes-by-category.md)
