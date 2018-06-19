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
ms.openlocfilehash: 0dcaa0aaf903787549cc91ffd19a34aa4aa066bd
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33384713"
---
# <a name="tn011-using-mfc-as-part-of-a-dll"></a>TN011: używanie MFC jako części biblioteki DLL
Ta uwaga opisuje regularne biblioteki DLL MFC, która pozwala na korzystanie z biblioteki MFC jako części biblioteki dołączanej (dynamicznie DLL) systemu Windows. Przyjęto założenie, że czytelnik zna biblioteki DLL systemu Windows i sposób ich tworzenia. Informacje o bibliotekach DLL rozszerzeń MFC, z której można utworzyć rozszerzenia do biblioteki MFC dla [biblioteki DLL wersji biblioteki MFC](../mfc/tn033-dll-version-of-mfc.md).  
  
## <a name="dll-interfaces"></a>Interfejsy biblioteki DLL  
 regularne biblioteki DLL MFC założono interfejsy między aplikacją a biblioteki DLL są określone w funkcji typu C lub jawnie wyeksportowanej klasy. Nie można wyeksportować interfejsy klas MFC.  
  
 Jeśli zarówno biblioteki DLL i aplikacji chcesz używać MFC, mają wybór albo przy użyciu udostępnionych wersji biblioteki MFC lub statycznie łączyć się kopii bibliotek. Aplikacji i biblioteki DLL może jednocześnie użyć jednej z standardowe wersje biblioteki MFC.  
  
 regularne biblioteki DLL MFC ma kilka zalet:  
  
-   Aplikacja korzystająca z biblioteki DLL nie trzeba używać MFC i musi być aplikacji Visual C++.  
  
-   Z regularne biblioteki DLL MFC, która łączy statycznie z MFC rozmiar pliku dll zależy od tylko procedury MFC i C środowiska uruchomieniowego, które są używane i połączone.  
  
-   Regularne biblioteki DLL MFC, która łączy dynamicznie z MFC oszczędności w pamięci z udostępnionego wersji MFC może być istotne. Jednak musisz przeprowadzić dystrybucję udostępnionej biblioteki DLL Mfc*\<wersji >* dll i Msvvcrt*\<wersji >* dll z biblioteki DLL.  
  
-   Projekt biblioteki DLL nie zależy od sposobu implementacji klasy. Eksportuje projektu biblioteki DLL tylko dla interfejsów API, ma. W związku z tym zmiana implementacji MFC DLL są nadal ważne.  
  
-   Z regularne biblioteki DLL MFC, która łączy statycznie z MFC użycie zarówno aplikacji, jak i biblioteki DLL MFC, że nie występują problemy z aplikacją, która chce innej wersji biblioteki MFC DLL lub na odwrót. Biblioteki MFC statycznie połączonej do każdej biblioteki DLL lub EXE, nie istnieje żadne pytanie, która wersja ma.  
  
## <a name="api-limitations"></a>Ograniczenia interfejsu API  
 Niektóre funkcje MFC nie ma zastosowania do wersji biblioteki DLL, albo z powodu ograniczeń technicznych lub ponieważ usługi te są zwykle dołączone przez aplikację. W bieżącej wersji biblioteki MFC, jest jedyną funkcją, która nie ma zastosowania `CWinApp::SetDialogBkColor`.  
  
## <a name="building-your-dll"></a>Tworzenie biblioteki DLL  
 W przypadku kompilowania kodu regularne biblioteki DLL MFC, która łączy statycznie z MFC, symbole `_USRDLL` i `_WINDLL` musi być zdefiniowany. Kod biblioteki DLL musi być również skompilowana z następujących przełączników kompilatora:  
  
- **/ D_WINDLL** oznacza kompilacji jest przeznaczony dla biblioteki DLL  
  
- **/ D_USRDLL** określa tworzysz regularną bibliotekę DLL MFC  
  
 Należy zdefiniować te symbole i korzystanie z tych przełączników kompilatora podczas kompilowania regularne biblioteki DLL MFC, która łączy dynamicznie z MFC. Ponadto symbol `_AFXDLL` musi być zdefiniowana i kod biblioteki DLL muszą być kompilowana przy użyciu:  
  
- **/ D_AFXDLL** Określa, czy tworzysz regularne biblioteki DLL MFC, która łączy dynamicznie z MFC  
  
 Musi być jawnie eksportowany interfejsów (API) między aplikacją a biblioteki DLL. Zaleca się definiowania interfejsów sieci o niskiej przepustowości i używać tylko interfejsów C, jeśli to możliwe. Bezpośrednie interfejsy C są łatwiejsze w obsłudze niż bardziej złożonych klas C++.  
  
 Umieść swoje interfejsy API w oddzielnych nagłówek, który może obejmować zarówno C i C++ plików. Zobacz nagłówek ScreenCap.h w przykładowym pojęcia zaawansowane MFC [DLLScreenCap](../visual-cpp-samples.md) przykład. Aby wyeksportować funkcji, wprowadź je w `EXPORTS` sekcja pliku definicji modułu (. DEF) lub obejmują `__declspec(dllexport)` w definicji funkcji. Użyj `__declspec(dllimport)` do importowania tych funkcji do pliku wykonywalnego klienta.  
  
 Należy dodać `AFX_MANAGE_STATE` makro na początku eksportowane funkcje w zwykłych bibliotekach DLL MFC, która łączy dynamicznie z MFC. To makro ustawia bieżący stan modułu dla biblioteki DLL. Aby użyć tego makra, Dodaj następujący wiersz kodu na początku funkcji wyeksportowanych z biblioteki DLL:  
  
 `AFX_MANAGE_STATE(AfxGetStaticModuleState( ))`  
  
## <a name="winmain---dllmain"></a>WinMain -> DllMain  
 Biblioteki MFC definiuje standardowe Win32 `DllMain` punkt wejścia, który inicjuje Twojej [CWinApp](../mfc/reference/cwinapp-class.md) pochodnych obiektu jak w typowej aplikacji MFC. Umieść wszystkie inicjowania specyficznej dla biblioteki DLL w [InitInstance](../mfc/reference/cwinapp-class.md#initinstance) metodę jak w typowej aplikacji MFC.  
  
 Należy pamiętać, że [CWinApp::Run](../mfc/reference/cwinapp-class.md#run) mechanizm nie ma zastosowania do biblioteki DLL, ponieważ aplikacja jest właścicielem pompa głównej wiadomości. Jeśli ma główne okno ramowe własnej biblioteki DLL lub wyświetla Niemodalne okna dialogowe, przekazywanie komunikatów głównego aplikacji należy wywołać procedury wyeksportowane biblioteki DLL, która wywołuje [CWinApp::PreTranslateMessage](../mfc/reference/cwinapp-class.md#pretranslatemessage).  
  
 Zobacz przykład DLLScreenCap do korzystania z tej funkcji.  
  
 `DllMain` Funkcja udostępniająca MFC wywoła [CWinApp::ExitInstance](../mfc/reference/cwinapp-class.md#exitinstance) metody klasy, która jest pochodną `CWinApp` przed biblioteki DLL jest zwalniany.  
  
## <a name="linking-your-dll"></a>Łączenie biblioteki DLL  
 Z regularne biblioteki DLL MFC, która łączy statycznie z MFC możesz połączyć biblioteki DLL z Nafxcwd.lib lub Nafxcw.lib i wersji środowiska uruchomieniowe C o nazwie Libcmt.lib. Biblioteki te są wstępnie skompilowany i może być zainstalowana, określając je po uruchomieniu Instalatora programu Visual C++.  
  
## <a name="sample-code"></a>Przykładowy kod  
 Zobacz przykład pojęcia zaawansowane MFC programu DLLScreenCap dla kompletnego przykładu. Oto kilka interesujące rzeczy do uwzględnienia w tym przykładzie:  
  
-   Flagi kompilatora biblioteki dll, a także aplikacji są różne.  
  
-   Linie łączy i. DEF, pliki DLL i dla aplikacji są różne.  
  
-   W języku C++ nie ma aplikacji, która używa biblioteki DLL.  
  
-   Interfejs pomiędzy aplikacją i biblioteki DLL jest interfejs API, który jest obsługiwany przez C lub C++ i został wyeksportowany z DLLScreenCap.def.  
  
 Poniższy przykład przedstawia interfejs API, który jest zdefiniowany w zwykły biblioteki MFC DLL, która łączy statycznie z MFC. W tym przykładzie deklaracja jest ujęta w `extern "C" { }` blok dla użytkowników C++. Daje to kilka korzyści. Po pierwsze ułatwia swoje interfejsy API biblioteki DLL można używać przez aplikacje klienckie z systemem innym niż C++. Po drugie jego zmniejsza obciążenie związane z biblioteki DLL, ponieważ przekręcona nazwa C++, nie zostaną zastosowane do wyeksportowanego nazwy. Ponadto ułatwi jawnie dodać do. DEF plików (w przypadku eksportowania według liczby porządkowej) bez konieczności martwić przekręcona nazwa.  
  
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
  
 Struktury używane przez interfejs API nie jest pochodną klasy MFC i są zdefiniowane w nagłówku interfejsu API. Zmniejsza złożoność interfejs między biblioteki DLL i aplikacji oraz powoduje, że plik DLL, który można używać przez C — programy.  
  
## <a name="see-also"></a>Zobacz też  
 [Uwagi techniczne według numerów](../mfc/technical-notes-by-number.md)   
 [Uwagi techniczne według kategorii](../mfc/technical-notes-by-category.md)

