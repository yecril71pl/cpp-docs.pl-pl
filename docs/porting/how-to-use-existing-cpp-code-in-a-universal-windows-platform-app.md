---
title: "Porady: używanie istniejącego kodu C++ w aplikacji platformy uniwersalnej systemu Windows | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: 87e5818c-3081-42f3-a30d-3dca2cf0645c
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 67bed0f5cc3ad07ae7b726b9e120aa56120186e6
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2018
---
# <a name="how-to-use-existing-c-code-in-a-universal-windows-platform-app"></a>Porady: używanie istniejącego kodu C++ w aplikacji platformy uniwersalnej systemu Windows
Najprostszym sposobem pobrania programu pulpitu w środowisku platformy uniwersalnej systemu Windows jest prawdopodobnie użycie technologii Mostek pulpitu. Obejmują one konwertera aplikacji pulpitu będzie pakietu istniejącej aplikacji jako aplikację platformy uniwersalnej systemu Windows bez kodu wymagane zmiany. Aby uzyskać więcej informacji, zobacz [przełączyć aplikację pulpitu do systemu Windows platformy Uniwersalnej z Mostek pulpitu](https://msdn.microsoft.com/windows/uwp/porting/desktop-to-uwp-root).

Pozostała część tego tematu opisano sposób portu biblioteki języka C++ (biblioteki dll i biblioteki statyczne) do uniwersalnych platformy systemu Windows (UWP). Można to zrobić, dzięki czemu podstawowych logiki C++ może być używany z wielu aplikacji platformy uniwersalnej systemu Windows. 
  
 Uruchamianie aplikacji platformy uniwersalnej systemu Windows w chronionym środowisku i w związku z tym wiele wywołań Win32 i COM, CRT interfejsu API, które mogłyby naruszyć bezpieczeństwo platformy są niedozwolone. Kompilator mogą wykrywać takie połączenia i generuje błąd, jeśli jest używana opcja /ZW. Zestaw certyfikacji aplikacji dla aplikacji służy do wykrywania kodu, który wywołuje interfejsy API zabronione. Zobacz [przy użyciu zestawu certyfikacji aplikacji](https://msdn.microsoft.com/library/windows/apps/hh694081.aspx).  
  
 Kod źródłowy jest dostępny dla biblioteki, można wyeliminować niedozwolonych wywołań interfejsu API. Aby uzyskać więcej informacji, łącznie z listą interfejsów API, które ma być dozwolony lub zabroniony, zobacz [platformy Uniwersalnej aplikacji Win32 i COM dla środowiska uruchomieniowego aplikacji systemu Windows i Universal Windows](https://msdn.microsoft.com/library/windows/apps/br205762.aspx) i [funkcje CRT, nie są obsługiwane w platformy uniwersalnej systemu Windows aplikacje](../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md). Niektóre rozwiązań alternatywnych można znaleźć w folderze [alternatywy dla interfejsów API systemu Windows w aplikacjach platformy uniwersalnej systemu Windows](/uwp/win32-and-com/alternatives-to-windows-apis-uwp).  
  
 Jeśli spróbujesz, można dodać odwołania z uniwersalnych projektów systemu Windows do klasycznego biblioteki pulpitu, otrzymasz komunikat o błędzie z informacją, że biblioteka nie jest zgodny. W przypadku biblioteki statycznej można połączyć z biblioteki po prostu dodając biblioteki (pliku lib) dane wejściowe konsolidatora, tak samo jak w klasycznym aplikacją systemu Win32. W przypadku bibliotek, gdy są dostępne tylko w pliku binarnym jest tylko opcja. Biblioteka statyczna jest połączony plik wykonywalny aplikacji, ale DLL Win32, która korzystać w aplikacji platformy uniwersalnej systemu Windows muszą być spakowane w aplikacji przez włączenie jej w projekcie i oznaczenie jej jako zawartości. Aby załadować biblioteki DLL Win32 w aplikacji platformy uniwersalnej systemu Windows, należy wywołać [LoadPackagedLibrary](https://msdn.microsoft.com/library/windows/desktop/hh447159.aspx) zamiast LoadLibrary lub LoadLibraryEx.  
  
 Jeśli masz kod źródłowy dla biblioteki DLL lub biblioteką statyczną, należy ponownie skompilować z parametrem /ZW jako projekt platformy uniwersalnej systemu Windows. Można to zrobić, można dodać odwołania w Eksploratorze rozwiązań i użyć go w aplikacji platformy uniwersalnej systemu Windows w języku C++. W przypadku biblioteki DLL Połącz z biblioteką eksportu.  
  
 Aby udostępnić funkcje dotyczące obiektów wywołujących w innych językach, biblioteki można przekonwertować na składnika środowiska wykonawczego systemu Windows. Składniki środowiska uruchomieniowego systemu Windows różnią się od zwykłej biblioteki DLL są umieszczane w formie plików winmd, które opisują zawartość w taki sposób, który wymaga platformy .NET i JavaScript konsumentów metadanych. Aby udostępnić elementów interfejsu API dla innych języków, można dodać C + +/ CX konstrukcje, takich jak klasy ref i opublikowania lub użyj [Windows środowiska uruchomieniowego C++ szablonu biblioteki (WRL)](../windows/windows-runtime-cpp-template-library-wrl.md).  W systemie Windows 10 i nowszych można użyć [C + +/ biblioteki WinRT](https://github.com/microsoft/cppwinrt) zamiast C + +/ CX. 
  
 Poprzedniego dyskusji nie ma zastosowania w przypadku składniki modelu COM, które muszą być obsługiwane inaczej. Jeśli masz serwer COM, EXE lub DLL, użytkownik może być używany w uniwersalnych projektów systemu Windows tak długo, jak go jako pakietu [składnika modelu COM bez rejestrowania](https://msdn.microsoft.com/library/dd408052.aspx), dodaj go do projektu jako plik zawartości i za pomocą wystąpienia [ Procedury CoCreateInstanceFromApp](https://msdn.microsoft.com/library/windows/apps/hh404137.aspx). Zobacz [w projektach C++ Sklepu Windows za pomocą biblioteki DLL COM bez](http://blogs.msdn.com/b/win8devsupport/archive/2013/05/20/using-free-com-dll-in-windows-store-c-project.aspx).  
  
 Jeśli masz istniejącej biblioteki COM przewidzianą do portu na platformy uniwersalnej systemu Windows, można go przekonwertować na składnika środowiska wykonawczego systemu Windows przy użyciu [Windows środowiska uruchomieniowego C++ szablonu biblioteki (WRL)](../windows/windows-runtime-cpp-template-library-wrl.md). Biblioteki WRL nie obsługuje wszystkich funkcji ATL i OLE, więc czy możliwe jest takiego portu zależy od ilości kodu COM jest zależna od com, ATL, jakie funkcje i OLE składnika wymaga.  
  
 Są to różne sposoby, czy można użyć istniejącego kodu C++ w projekty platformy UWP. Niektóre metody nie wymagają kodu do ponownej kompilacji z rozszerzeniami składnika (C + +/ CX) włączone (czyli z parametrem /ZW opcja), a niektóre zrobić, jeśli należy zachować kodu w języku C++ standard lub zachować klasyczne środowisko kompilacji Win32 dla części kodu, możesz to zrobić , architektura odpowiednie opcje. Na przykład kodu, który zawiera interfejsu użytkownika platformy uniwersalnej systemu Windows i typy, które mają być ujawniony dla kodu C#, Visual Basic i JavaScript powinny być w projektach aplikacji systemu Windows i projekty składnika środowiska wykonawczego systemu Windows. Kod, który ma być używane tylko w języku C++ (w tym języku C + +/ CX) kodu może być projektu, który kompiluje się z opcją wx lub standardowy projektu C++. Tylko do pliku binarnego kodu może być używany, łącząc go jako bibliotekę statyczną, lub z aplikacji jako zawartości i załadowany w bibliotece DLL tylko wtedy, gdy nie korzysta z interfejsów API zabronione.  
  
 Niezależnie od tego, które z tych scenariuszy programowania, możesz wybrać należy zwrócić uwagę liczbę definicje makr, które można użyć w kodzie, dzięki czemu można skompilować kod warunkowo zarówno w obszarze klasycznej Win32 pulpitu i platformy uniwersalnej systemu Windows.  
  
```cpp  
#if WINAPI_FAMILY_PARTITION(WINAPI_PARTITION_PC_APP)  
#if WINAPI_FAMILY_PARTITION(WINAPI_PARTITION_PHONE_APP)  
#if WINAPI_FAMILY_PARTITION(WINAPI_PARTITION_APP)  
#if WINAPI_FAMILY_PARTITION(WINAPI_PARTITION_DESKTOP)  
```  
  
 Te instrukcje odpowiednio mają zastosowanie do aplikacji platformy uniwersalnej systemu Windows, Sklep Windows Phone aplikacje, zarówno lub żadna (klasycznej Win32 tylko wersja desktop). Makra te są dostępne tylko w systemie Windows 8.1 SDK i nowszych, jeśli kod wymaga kompilacji z wcześniejszych wersji zestawu Windows SDK lub dla innych platform, oprócz systemu Windows, należy również rozważyć przypadku że żaden z nich, a następnie są zdefiniowane.  
  
 Ten temat zawiera poniższe procedury.  
  
1.  [Przy użyciu Win32 biblioteki DLL w aplikacji platformy uniwersalnej systemu Windows](#BK_Win32DLL)  
  
2.  [Przy użyciu natywnej biblioteki statycznej C++ w aplikacji platformy uniwersalnej systemu Windows](#BK_StaticLib)  
  
3.  [Eksportowanie biblioteki C++ do składnika środowiska wykonawczego systemu Windows](#BK_WinRTComponent)  
  
##  <a name="BK_Win32DLL">Przy użyciu Win32 biblioteki DLL w aplikacji platformy uniwersalnej systemu Windows</a>  
 Dla lepszej bezpieczeństwa i niezawodności uniwersalnych aplikacji systemu Windows uruchamiana w środowisku ograniczeniami środowiska uruchomieniowego, nie można po prostu użyć dowolnego natywnej biblioteki DLL sposób, jak w klasycznej aplikacji pulpitu systemu Windows. Jeśli masz kod źródłowy dla biblioteki DLL może portu kod, aby była uruchamiana na platformy uniwersalnej systemu Windows. Należy najpierw zmienić kilka ustawień projektu i metadanych pliku projektu do identyfikowania projektu jako projektu platformy uniwersalnej systemu Windows. Należy skompilować kod biblioteki przy użyciu opcji /ZW, dzięki czemu C + +/ CX. Niektóre wywołania interfejsu API nie są dozwolone w aplikacji platformy uniwersalnej systemu Windows ze względu na bardziej restrykcyjne kontrolki skojarzone z tym środowisku. Zobacz [Win32 i COM dla środowiska wykonawczego systemu Windows aplikacji i uniwersalnych systemu Windows aplikacji platformy Uniwersalnej](https://msdn.microsoft.com/library/windows/apps/br205757.aspx).  
  
 Poniższa procedura ma zastosowanie w przypadku, gdy masz natywnej biblioteki DLL, która udostępnia funkcje przy użyciu atrybutu __declspec(dllexport).  
  
#### <a name="to-port-a-native-dll-to-the-uwp-without-creating-a-new-project"></a>Do portu natywnej biblioteki DLL do platformy uniwersalnej systemu Windows bez tworzenia nowego projektu  
  
1.  Jeśli masz natywnej biblioteki DLL, które eksportuje funkcji przy użyciu __declspec(dllexport) tych funkcji można wywołać z aplikacji platformy uniwersalnej systemu Windows przez ponowną kompilację biblioteki DLL jako projekt platformy uniwersalnej systemu Windows. Na przykład załóżmy, że mamy biblioteki DLL, które eksportuje kilka klas i ich metod z kodem, takich jak następujący plik nagłówka:  
  
    ```  
    // giraffe.h  
    #pragma once  
  
    #ifdef _DLL  
    #define GIRAFFE_API __declspec(dllexport)  
    #else  
    #define GIRAFFE_API   
    #endif  
  
    GIRAFFE_API int giraffeFunction();  
  
    class Giraffe  
    {  
        int id;  
            Giraffe(int id_in);  
        friend class GiraffeFactory;  
  
    public:  
        GIRAFFE_API int GetID();  
    };  
  
    class GiraffeFactory  
    {  
        static int nextID;  
    
    public:  
        GIRAFFE_API GiraffeFactory();  
        GIRAFFE_API static int GetNextID();  
        GIRAFFE_API static Giraffe* Create();  
   };  
    ```  
  
     I następujący plik kodu:  
  
    ```  
    // giraffe.cpp  
    #include "stdafx.h"  
    #include "giraffe.h"  
  
    Giraffe::Giraffe(int id_in) : id(id_in)  
    {  
    }  
  
    int Giraffe::GetID()  
    {  
      return id;  
    }  
  
    int GiraffeFactory::nextID = 0;  
  
    GiraffeFactory::GiraffeFactory()  
    {  
        nextID = 0;  
    }  
  
    int GiraffeFactory::GetNextID()  
    {  
        return nextID;  
    }  
  
    Giraffe* GiraffeFactory::Create()  
    {  
        return new Giraffe(nextID++);  
    }  
  
    int giraffeFunction();  
    ```  
  
     Wszystkie inne w projekcie (stdafx.h, dllmain.cpp) jest częścią standardowego szablonu projektu Win32. Jeśli chcesz z niego skorzystać, ale nie chcesz używać własnych bibliotek DLL jeszcze dalszych kroków, spróbuj utworzyć projekt Win32, wybierz biblioteki DLL w Kreatorze projektu następnie dodać nagłówka pliku giraffe.h i kod pliku giraffe.cpp i skopiuj zawartość z kodu w tym kroku w aplikacji pliki ropriate.  
  
     Kod definiuje makro GIRAFFE_API, który jest rozpoznawany jako __declspec(dllexport) po _DLL zdefiniowano (gdy projekt jest budowany jako biblioteki DLL).  
  
2.  Otwórz właściwości projektu dla projektu biblioteki DLL i ustaw dla konfiguracji **wszystkie konfiguracje**.  
  
3.  We właściwościach projektu w obszarze **C/C++**, **ogólne** ustaw **korzystać rozszerzenie środowiska uruchomieniowego systemu Windows** do **tak (/ZW)**. Dzięki temu składnik rozszerzeń (C + +/ CX).  
  
4.  W **Eksploratora rozwiązań**, wybierz węzeł projektu, otwórz menu skrótów i wybierz polecenie **Zwolnij projekt**. Następnie otwórz menu skrótów węzła projektu zwolnione i wybierz edytować plik projektu. Znajdź WindowsTargetPlatformVersion element i Zamień następujące elementy.  
  
    ```xml  
    <AppContainerApplication>true</AppContainerApplication>  
    <ApplicationType>Windows Store</ApplicationType>  
    <WindowsTargetPlatformVersion>10.0.10156.0</WindowsTargetPlatformVersion>  
    <WindowsTargetPlatformMinVersion>10.0.10156.0</WindowsTargetPlatformMinVersion>  
    <ApplicationTypeRevision>10.0</ApplicationTypeRevision>  
    ```  
  
     Zamknij plik .vcxproj, ponownie otwórz menu skrótów i wybierz polecenie **Załaduj ponownie projekt**.  
  
     Eksplorator rozwiązań identyfikuje projekt jako projekt uniwersalnej systemu Windows.  
  
5.  Upewnij się, że nazwy prekompilowanego nagłówka pliku jest poprawna. W sekcji prekompilowanych nagłówków zmienić prekompilowany plik nagłówka z pch.h na stdafx.h. Jeśli nie zrobisz, zostanie wyświetlony następujący błąd.  
  
    ```Output  
    error C2857: '#include' statement specified with the /Ycpch.h command-line option was not found in the source file  
    ```  
  
     Problem polega na tym, że projektów uniwersalnych systemu Windows użyj konwencję nazewnictwa dla prekompilowanego pliku nagłówkowego.  
  
6.  Skompiluj projekt. Można otrzymać niektóre błędy dotyczące opcji wiersza polecenia niezgodne. Na przykład często używanych opcji Włącz minimalnego odbudować (/ Gm) jest domyślnie ustawiony w wielu projektach C++ i jest niezgodny z parametrem /ZW.  
  
     Niektóre funkcje nie są dostępne podczas kompilowania dla platformy uniwersalnej systemu Windows. Zostanie wyświetlone błędy kompilatora o wszelkich problemach. Tych adresów aż do uzyskania czystą kompilację.  
  
7.  Aby korzystać z biblioteki DLL w aplikacji platformy uniwersalnej systemu Windows, w tym samym rozwiązaniu, otwórz menu skrótów węzła projektu platformy uniwersalnej systemu Windows i wybierz **dodać, odwołanie**.  
  
     W obszarze **projektów, rozwiązań**, zaznacz pole wyboru obok projektu biblioteki DLL i wybierz **OK** przycisku.  
  
8.  Dołącza plik(i) nagłówka biblioteki w pliku pch.h aplikacji platformy uniwersalnej systemu Windows.  
  
    ```  
    #include "..\MyNativeDLL\giraffe.h"  
    ```  
  
9. Dodaj kod w zwykły sposób, w projekcie platformy uniwersalnej systemu Windows, aby wywoływać funkcje i utworzy typy z biblioteki DLL.  
  
    ```  
    MainPage::MainPage()  
    {  
        InitializeComponent();  
        GiraffeFactory gf;  
        Giraffe* g = gf.Create();  
        int id = g->GetID();  
    }  
  
    ```  
  
##  <a name="BK_StaticLib">Przy użyciu natywnej biblioteki statycznej C++ w aplikacji platformy uniwersalnej systemu Windows</a>  
 Można używać natywnej biblioteki statycznej C++ w projekcie platformy uniwersalnej systemu Windows, ale istnieją pewne ograniczenia i pod uwagę. Początek przeczytaj to [tematu](https://msdn.microsoft.com/library/hh771041.aspx) o bibliotekach statycznych w języku C + +/ CX. Kod macierzysty w bibliotece statycznej można korzystać z aplikacji platformy uniwersalnej systemu Windows, ale nie zaleca się tworzenia typów publicznych ref w bibliotece statycznej. Jeśli kompilacja biblioteki statycznej z opcją /ZW, ostrzega bibliotekarza (faktycznie konsolidator kamuflażu):  
  
```  
LNK4264: archiving object file compiled with /ZW into a static library; note that when authoring Windows Runtime types it is not recommended to link with a static library that contains Windows Runtime metadata  
```  
  
 Można jednak użyć biblioteki statycznej w platformy uniwersalnej systemu Windows bez konieczności ponownego kompilowania z parametrem /ZW. Nie można zadeklarować wszystkie typy ref lub korzystania z języka C + +/ CX konstrukcje, ale jeśli Twoje ma na celu po prostu użyć biblioteki kodu natywnego, a następnie należy wykonać następujące kroki.  
  
#### <a name="to-use-a-native-c-static-library-in-a-uwp-project"></a>Aby użyć natywnej biblioteki statycznej C++ w projekcie platformy UWP  
  
1.  We właściwościach projektu dla projektu platformy uniwersalnej systemu Windows, w sekcji konsolidatora Dodaj ścieżkę do biblioteki we właściwości danych wejściowych. Na przykład dla biblioteki w projekcie, który umieszcza dane wyjściowe w *SolutionFolder*\Debug\MyNativeLibrary\MyNativeLibrary.lib, Dodaj ścieżkę względną `Debug\MyNativeLibrary\MyNativeLibrary.lib`.  
  
2.  Dodaj instrukcję Dołącz do odwoływania się do pliku nagłówka do Twojej pch.h w projekcie platformy uniwersalnej systemu Windows i zacząć dodawać kod, który korzysta z biblioteki.  
  
    ```  
    #include "..\MyNativeLibrary\giraffe.h"  
    ```  
  
     Nie dodawaj odwołanie w **odwołania** w węźle **Eksploratora rozwiązań**. Ten mechanizm działa tylko dla składników środowiska wykonawczego systemu Windows.  
  
##  <a name="BK_WinRTComponent">Eksportowanie biblioteki C++ do składnika środowiska wykonawczego systemu Windows</a>  
 Jeśli chcesz korzystać z natywnych interfejsów API w bibliotece statycznej z aplikacji platformy uniwersalnej systemu Windows, a masz kod źródłowy dla natywnej biblioteki, można portu kod do składnika środowiska wykonawczego systemu Windows. Nie będzie już bibliotekę statyczną, będzie on biblioteki DLL. Może być używany w dowolnej aplikacji platformy uniwersalnej systemu Windows w języku C++, ale inaczej niż w przypadku biblioteki statycznej, można dodać typy ref i innych C + +/ CX konstrukcje, które są dostępne dla klientów w kodzie do aplikacji platformy uniwersalnej systemu Windows, niezależnie od języka. W związku z tym są dostępne następujące typy C#, Visual Basic lub JavaScript.  Podstawowa procedura polega na Utwórz projekt składnika środowiska wykonawczego systemu Windows, skopiuj do niego kod biblioteki statycznej i rozwiązać wszelkie błędy, które wynikają z przenoszenie kodu z kompilacji standard C++ do kompilacji /ZW.  
  
#### <a name="to-port-a-c-library-to-a-windows-runtime-component"></a>Do portu biblioteki C++ do składnika środowiska wykonawczego systemu Windows  
  
1.  Utwórz projekt składnika środowiska wykonawczego systemu Windows.  
  
2.  Zamknij projekt.  
  
3.  W Eksploratorze plików systemu Windows znajdź projektu. Domyślnie program Visual Studio używa folderu 2017\Projects programu Visual Studio w folderze dokumenty. Zlokalizuj projektu biblioteki C++, który zawiera kod, który chcesz dodać port. Skopiuj pliki źródłowe (pliki nagłówkowe, pliki kodu i innych zasobów, w tym w podkatalogach) z projektu biblioteki języka C++, a następnie wklej je do folderu projektu, upewniając się zachować taką samą strukturę folderów.  
  
4.  Otwórz projekt składnika środowiska wykonawczego systemu Windows, a następnie otwórz menu skrótów węzła projektu w **Eksploratora rozwiązań**i wybierz polecenie **Dodaj, istniejący element**.  
  
5.  Zaznacz wszystkie pliki, aby dodać z oryginalnego projektu, a następnie kliknij przycisk OK. Powtórz w razie potrzeby dla podfolderów.  
  
6.  Użytkownik może teraz mają niektóre zduplikowane kodu. Jeśli masz więcej niż jeden prekompilowanego nagłówka (np. stdafx.h i pch.h), wybierz jedną do zachowania. Skopiuj dowolny kod wymagane, takie jak zawiera instrukcje do tego, który jest zachowywana. Następnie, w obszarze usuwanie właściwości innych i w projekcie **prekompilowanych nagłówków**, upewnij się, że nazwa pliku nagłówka jest poprawna.  
  
     Jeśli zmienisz plik, który będzie używany jako prekompilowanego nagłówka, upewnij się, że opcje prekompilowanego nagłówka są poprawne dla każdego pliku. Wybierz kolejno każdy plik .cpp, otworzyć okno właściwości i upewnij się, że wszystkie są ustawione na **Użyj (/Yu)**, z wyjątkiem żądaną prekompilowanego nagłówka, który powinien być ustawiony na **Utwórz (/Yc)**.  
  
7.  Skompiluj projekt i usuń wszelkie błędy. Te błędy, może być spowodowane przy użyciu opcji /ZW lub może być spowodowane przez nową wersję zestawu Windows SDK lub może odzwierciedlają zależności, takich jak pliki nagłówkowe, które zależy od biblioteki lub różnice w ustawieniach projektu projektu stary i nowy o ne.  
  
8.  Dodaj typy publiczne odwołania do projektu lub konwersji typów zwykłej dla typów ref, aby udostępnić punkty wejścia do funkcji, którą chcesz się połączyć z aplikacji platformy uniwersalnej systemu Windows.  
  
9. Przetestuj składnika, dodając do niego odwołanie z projektu aplikacji platformy uniwersalnej systemu Windows i dodać kod do wywołania publiczne interfejsy API, został utworzony.  
  
## <a name="see-also"></a>Zobacz też  
 [Przenoszenie na platformę uniwersalną systemu Windows](../porting/porting-to-the-universal-windows-platform-cpp.md)