---
title: 'TN011: Używanie MFC jako części biblioteki DLL | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.mfc.dll
dev_langs:
- C++
helpviewer_keywords:
- _USRDLL symbol
- USRDLLs, compiler switches
- TN011
- DLLs [MFC], linking
- MFC DLLs [MFC], linking regular MFC DLLs to MFC
ms.assetid: 76753e9c-59dc-40f6-b6a7-f6bb9a7c4190
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e476f456b849c0a5564b59ceae21faed26dc3d34
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50062135"
---
# <a name="tn011-using-mfc-as-part-of-a-dll"></a>TN011: używanie MFC jako części biblioteki DLL

Ta uwaga opisuje regularne biblioteki DLL MFC, które umożliwiają korzystanie z biblioteki MFC jako części Windows biblioteki dołączanej (dynamicznie DLL). Przyjęto założenie, że znasz biblioteki dll Windows i jak je tworzyć. Uzyskać informacji o biblioteki DLL rozszerzeń MFC, dzięki którym możesz tworzyć rozszerzenia do biblioteki MFC, zobacz [wersji MFC DLL](../mfc/tn033-dll-version-of-mfc.md).

## <a name="dll-interfaces"></a>Interfejsy biblioteki DLL

regularne biblioteki DLL MFC przyjęto założenie, interfejsy między aplikacją a biblioteki DLL są określone w funkcji języka C jak lub jawnie eksportowane klasy. Nie można wyeksportować interfejsu klasy MFC.

Jeśli biblioteka DLL i aplikacji używać klasy MFC, mają wyboru, aby korzystać z udostępnionych wersji biblioteki MFC, lub statycznie połączyć kopię biblioteki. Aplikacji i bibliotek DLL może jednocześnie użyć jednej z standardowe wersje biblioteki MFC.

regularne biblioteki DLL MFC mają kilka zalet:

- Aplikacji, która używa biblioteki DLL nie będzie musiał używać klasy MFC i nie musi być aplikacji Visual C++.

- Za pomocą regularne biblioteki DLL MFC, które będą statycznie łączyć się z MFC rozmiar pliku dll zależy od tylko procedury czasu wykonywania MFC i C, które są używane i połączone.

- Za pomocą regularne biblioteki DLL MFC, która łączy dynamicznie MFC oszczędności pamięci wynikające z wykorzystania udostępnionej wersja MFC mogą być znaczące. Jednakże, należy go rozesłać udostępnionych bibliotek DLL Mfc*\<wersji >*.dll i Msvvcrt*\<wersji >*.dll z biblioteką DLL.

- Projekt DLL jest niezależny od implementacji klasy. Projekt DLL eksportuje tylko do interfejsów API mają. W wyniku implementacji zmiany zwykłych bibliotekach MFC DLL są nadal ważne.

- Przy użyciu zwykłych bibliotekach MFC dll, która statycznie łączy się z MFC użycie aplikacji i bibliotek DLL MFC, że nie występują problemy z aplikacją, która chce inną wersję biblioteki MFC DLL lub na odwrót. Biblioteka MFC statycznie połączoną do każdej biblioteki DLL lub EXE, nie istnieje żadne pytanie o wersji, które mają.

## <a name="api-limitations"></a>Ograniczenia interfejsu API

Niektóre funkcje MFC nie ma zastosowania do wersji biblioteki DLL, albo z powodu ograniczeń technicznych lub ponieważ te usługi są zazwyczaj dostarczane przez aplikację. Za pomocą bieżącej wersji MFC jest tylko funkcja, która nie ma zastosowania `CWinApp::SetDialogBkColor`.

## <a name="building-your-dll"></a>Kompilowanie biblioteki DLL

Podczas kompilowania zwykłych bibliotekach MFC dll, która statycznie łączy z MFC, symbole `_USRDLL` i `_WINDLL` musi być zdefiniowany. Kod biblioteki DLL, również muszą być skompilowane przy użyciu następujących przełączników kompilatora:

- **/ D_WINDLL** oznacza kompilacji jest dla biblioteki DLL

- **/ D_USRDLL** określa tworzysz regularnej biblioteki DLL MFC

Należy także zdefiniować te symbole i używać tych przełączników kompilatora, podczas kompilowania zwykłych bibliotekach MFC dll, która łączy dynamicznie MFC. Ponadto symbol `_AFXDLL` muszą być zdefiniowane i kod biblioteki DLL muszą być skompilowane przy użyciu:

- **/ D_AFXDLL** Określa, czy tworzysz zwykłej biblioteki MFC DLL, która łączy dynamicznie z MFC

Interfejsy API między aplikacją a biblioteki DLL musi być jawnie eksportowany. Firma Microsoft zaleca definiowanie interfejsów sieci o niskiej przepustowości się i używać tylko C interfejsów, jeżeli jest to możliwe. Bezpośrednie interfejsy C są łatwiejsze w obsłudze niż bardziej złożonych klasy C++.

Umieść swoje interfejsy API w oddzielnych nagłówka, który może być dołączony przez pliki C i C++. Zobacz nagłówek ScreenCap.h w próbce zaawansowanych koncepcji MFC [DLLScreenCap](../visual-cpp-samples.md) przykład. Aby wyeksportować funkcji, należy wprowadzić je w `EXPORTS` sekcji w pliku definicji modułu (. DEF), lub Uwzględnij `__declspec(dllexport)` w definicji funkcji. Użyj `__declspec(dllimport)` do importowania tych funkcji do pliku wykonywalnego klienta.

Na początku wszystkich eksportowanych funkcji w zwykłych bibliotekach MFC dll, która łączy dynamicznie MFC, należy dodać AFX_MANAGE_STATE — makro. To makro ustawia bieżący stan modułu dla biblioteki DLL. Aby użyć tego makra, należy dodać następujący wiersz kodu na początku funkcji wyeksportowanych z biblioteki DLL:

`AFX_MANAGE_STATE(AfxGetStaticModuleState( ))`

## <a name="winmain---dllmain"></a>WinMain -> DllMain

Biblioteka MFC definiuje standardowe Win32 `DllMain` punktu wejścia, który inicjuje swoje [CWinApp](../mfc/reference/cwinapp-class.md) pochodzi z obiektu, tak jak w typowej aplikacji MFC. Umieść wszystkie Inicjowanie biblioteki DLL określonej w [InitInstance](../mfc/reference/cwinapp-class.md#initinstance) metodę, tak jak w typowej aplikacji MFC.

Należy pamiętać, że [CWinApp::Run](../mfc/reference/cwinapp-class.md#run) mechanizm nie ma zastosowania do biblioteki DLL, ponieważ aplikacja jest właścicielem pompy komunikatów głównego. Jeśli biblioteka DLL ma główne okno ramowe własnych lub wyświetla Niemodalne okna dialogowe, pompy komunikatów główny aplikacji musi wywołać procedurę wyeksportowane biblioteki DLL, która wywołuje [CWinApp::PreTranslateMessage](../mfc/reference/cwinapp-class.md#pretranslatemessage).

Zobacz przykład DLLScreenCap korzystania z tej funkcji.

`DllMain` Funkcja udostępniająca MFC wywoła [CWinApp::ExitInstance](../mfc/reference/cwinapp-class.md#exitinstance) metody klasy, która jest pochodną `CWinApp` przed biblioteki DLL jest zwalniana.

## <a name="linking-your-dll"></a>Łączenie z biblioteki DLL

Za pomocą regularne biblioteki DLL MFC, które będą statycznie łączyć się z MFC musisz połączyć biblioteki DLL Nafxcwd.lib ani Nafxcw.lib oraz z wersją środowiska uruchomieniowego C o nazwie biblioteki Libcmt.lib. Biblioteki te są wstępnie skompilowane i mogą być zainstalowane, określając je, po uruchomieniu Instalatora programu Visual C++.

## <a name="sample-code"></a>Przykładowy kod

Zobacz próbce zaawansowanych koncepcji MFC program DLLScreenCap pełny przykład. Oto kilka interesujących rzeczy, należy pamiętać, w tym przykładzie:

- Flagi kompilatora biblioteki dll i tych aplikacji są różne.

- Linie łączy i. Pliki DEF dla biblioteki DLL i tych aplikacji są różne.

- Aplikacji, która używa biblioteki DLL nie musi być w języku C++.

- Interfejs między aplikacją a biblioteki DLL jest interfejs API, który jest używany przez C lub C++ i są eksportowane z DLLScreenCap.def.

Poniższy przykład ilustruje interfejsu API, który jest zdefiniowany w zwykłej biblioteki MFC DLL, która statycznie łączy się MFC. W tym przykładzie deklaracja jest ujęty w `extern "C" { }` blok dla użytkowników języka C++. To ma kilka zalet. Najpierw tworzy DLL interfejsów API można używać przez aplikacje klienckie C++ inny niż. Po drugie zmniejsza obciążenie DLL ponieważ dekorowanie nazw języka C++, nie będą stosowane do wyeksportowanego nazwy. Ponadto ułatwia jawnie dodać do. DEF pliku (w przypadku eksportowania według liczby porządkowej) bez konieczności martwienia się o dekorowanie nazw.

```
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

Struktury używane przez interfejs API nie pochodzą z klasy MFC i są definiowane w nagłówku interfejsu API. Zmniejsza złożoność interfejs między biblioteki DLL i aplikacji i sprawia, że biblioteka DLL można używać przez programy c.

## <a name="see-also"></a>Zobacz też

[Uwagi techniczne według numerów](../mfc/technical-notes-by-number.md)<br/>
[Uwagi techniczne według kategorii](../mfc/technical-notes-by-category.md)

