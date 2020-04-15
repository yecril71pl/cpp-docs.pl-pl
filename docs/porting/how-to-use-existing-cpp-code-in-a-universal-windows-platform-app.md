---
title: 'Porady: używanie istniejącego kodu C++ w aplikacji platformy uniwersalnej systemu Windows'
ms.date: 04/08/2019
ms.assetid: 87e5818c-3081-42f3-a30d-3dca2cf0645c
ms.openlocfilehash: b1351a1c7858b00cffc454fa66831b3995aea804
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366427"
---
# <a name="how-to-use-existing-c-code-in-a-universal-windows-platform-app"></a>Porady: używanie istniejącego kodu C++ w aplikacji platformy uniwersalnej systemu Windows

Być może najprostszym sposobem uruchomienia programu klasycznego w środowisku platformy uniwersalnej systemu Windows (UWP) jest użycie technologii Mostka pulpitu. Należą do nich konwerter aplikacji pulpitu, który będzie pakiet istniejącej aplikacji jako aplikacji platformy uniwersalnej systemu Windows bez zmian kodu wymagane. Aby uzyskać więcej informacji, zobacz [Desktop Bridge](/windows/uwp/porting/desktop-to-uwp-root).

W dalszej części tego tematu omówiono sposób przenoszenia bibliotek języka C++ (bibliotek DLL i bibliotek statycznych) do platformy uniwersalnej systemu Windows. Można to zrobić, aby podstawowa logika języka C++ może być używana z wieloma aplikacjami platformy uniwersalnej systemu Windows.

Aplikacje platformy uniwersalnej systemu Windows są uruchamiane w środowisku chronionym i w rezultacie wiele wywołań interfejsu API Win32, COM i CRT, które mogą naruszyć bezpieczeństwo platformy, nie jest dozwolonych. Kompilator może wykryć takie wywołania `/ZW` i wygenerować błąd, jeśli opcja jest używana. Za pomocą zestawu certyfikacji aplikacji w aplikacji można wykryć kod, który wywołuje niedozwolonych interfejsów API. Aby uzyskać więcej informacji, zobacz [Zestaw certyfikacji aplikacji systemu Windows](/windows/uwp/debug-test-perf/windows-app-certification-kit).

Jeśli kod źródłowy jest dostępny dla biblioteki, można wyeliminować zakazanych wywołań interfejsu API. Aby uzyskać szczegółowe informacje, w tym listę interfejsów API, które są dozwolone lub zabronione, zobacz [Interfejsy API win32 i COM dla aplikacji platformy uniwersalnej systemu Windows](/uwp/win32-and-com/win32-and-com-for-uwp-apps) i [funkcji CRT, które nie są obsługiwane w aplikacjach platformy uniwersalnej systemu Windows](../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md). Niektóre alternatywy można znaleźć w [alternatywy dla interfejsów API systemu Windows w aplikacjach platformy uniwersalnej](/uwp/win32-and-com/alternatives-to-windows-apis-uwp)systemu Windows .

Jeśli po prostu spróbujesz dodać odwołanie z programu Universal Windows Project do klasycznej biblioteki pulpitu, zostanie wyświetlony komunikat o błędzie informujący, że biblioteka nie jest zgodna. W przypadku biblioteki statycznej można połączyć się z biblioteką, dodając bibliotekę (plik lib) do danych wejściowych konsolidatora, tak jak w klasycznej aplikacji Win32. W przypadku bibliotek, w których dostępny jest tylko plik binarny, jest to jedyna opcja. Biblioteka statyczna jest połączona z plikiem wykonywalnym aplikacji, ale biblioteka DLL win32, która jest zużywana w aplikacji platformy uniwersalnej systemu Uniwersalnego, musi być spakowana do aplikacji przez włączenie jej do projektu i oznaczenie jej jako zawartości. Aby załadować bibliotekę DLL Win32 w aplikacji platformy uniwersalnej systemuśpiłnie, `LoadLibraryEx`należy również wywołać [LoadPackagedLibrary](/windows/win32/api/winbase/nf-winbase-loadpackagedlibrary) zamiast `LoadLibrary` lub .

Jeśli masz kod źródłowy biblioteki DLL lub biblioteki `/ZW` statycznej, można ponownie skompilować jako projekt platformy uniwersalnej systemu i platformy uniwersalnej systemu. Jeśli to zrobisz, można dodać odwołanie za pomocą **Eksploratora rozwiązań**i używać go w aplikacjach platformy uniwersalnej systemu Windows języka C++. W przypadku biblioteki DLL należy połączyć się z biblioteką eksportu.

Aby udostępnić funkcje wywołującym w innych językach, można przekonwertować bibliotekę na składnik środowiska wykonawczego systemu Windows. Składniki środowiska wykonawczego systemu Windows różnią się od zwykłych bibliotek DLL tym, że zawierają metadane w postaci plików .winmd, które opisują zawartość w sposób wymagany przez konsumentów platformy .NET i JavaScript. Aby udostępnić elementy interfejsu API innym językom, można dodać konstrukcje C++/CX, takie jak klasy ref, i upublicznić je lub użyć [biblioteki szablonów Środowiska Wykonawczego systemu Windows (WRL)](../windows/windows-runtime-cpp-template-library-wrl.md).  W systemie Windows 10 i nowszych można używać [biblioteki C++/WinRT](https://github.com/microsoft/cppwinrt) zamiast C++/CX.

Poprzedzająca dyskusja nie ma zastosowania do przypadku składników COM, które muszą być traktowane inaczej. Jeśli masz serwer COM w pliku EXE lub DLL, możesz go używać w uniwersalnym programie Windows Project, o ile spakowasz go jako [składnik COM bez rejestracji,](/windows/win32/sbscs/creating-registration-free-com-objects)dodaj go do projektu jako plik zawartości i skonkrzyjnie go za pomocą [CoCreateInstanceFromApp](/windows/win32/api/combaseapi/nf-combaseapi-cocreateinstancefromapp). Aby uzyskać więcej informacji, zobacz [Korzystanie z biblioteki DLL free-COM w programie Windows Store C++ Project](https://blogs.msdn.microsoft.com/win8devsupport/2013/05/19/using-free-com-dll-in-windows-store-c-project/).

Jeśli masz istniejącą bibliotekę COM, którą chcesz przenieść do platformy uniwersalnej systemu Windows, można przekonwertować ją na składnik środowiska wykonawczego systemu Windows przy użyciu [biblioteki szablonów WRL środowiska wykonawczego systemu Windows (WRL).](../windows/windows-runtime-cpp-template-library-wrl.md) WRL nie obsługuje wszystkich funkcji ATL i OLE, więc czy taki port jest możliwe zależy od tego, ile kodu COM zależy od jakich funkcji COM, ATL i OLE składnika wymaga.

Są to różne sposoby, które można użyć istniejącego kodu C++ w projektach platformy uniwersalnej systemu i platformy uniwersalnej systemu. Niektóre sposoby nie wymagają kodu do ponownej kompilacji z rozszerzeniami składników (C++/CX) włączone (to znaczy z `/ZW` opcją), a niektóre zrobić, więc jeśli trzeba zachować kod w standardzie C ++ lub zachować klasyczne środowisko kompilacji Win32 dla niektórych kodu, można to zrobić, z odpowiednimi wyborami architektury. Na przykład cały kod, który zawiera interfejs użytkownika platformy uniwersalnej systemu Windows i typy, które mają być narażone na c#, Visual Basic i JavaScript wywołań powinny być w projektach aplikacji systemu Windows i projektów składnika środowiska wykonawczego systemu Windows. Kod, który musi być używane tylko w języku C++ (w tym C++/CX) `/WX` kod może być w projekcie, który kompiluje z opcją lub standardowy projekt C++. Kod tylko binarny może służyć przez połączenie go jako biblioteki statycznej lub spakowane z aplikacją jako zawartość i ładowane w bibliotece DLL tylko wtedy, gdy nie używa zakazanych interfejsów API.

Niezależnie od tego, który z tych scenariuszy rozwoju wybrać, należy pamiętać o wielu definicjach makr, które można użyć w kodzie, dzięki czemu można skompilować kod warunkowo w obu klasycznych pulpitu Win32 i platformy uniwersalnej systemu Windows.

```cpp
#if WINAPI_FAMILY_PARTITION(WINAPI_PARTITION_PC_APP)
#if WINAPI_FAMILY_PARTITION(WINAPI_PARTITION_PHONE_APP)
#if WINAPI_FAMILY_PARTITION(WINAPI_PARTITION_APP)
#if WINAPI_FAMILY_PARTITION(WINAPI_PARTITION_DESKTOP)
```

Te instrukcje dotyczą odpowiednio aplikacji platformy uniwersalnej systemu Windows, aplikacji ze Sklepu Windows Phone, obu lub nie (tylko klasyczny pulpit Win32). Te makra są dostępne tylko w zestawie Windows SDK 8.1 lub nowszym, więc jeśli kod musi być kompilowany z wcześniejszymi wersjami zestawie Windows SDK lub dla innych platform oprócz systemu Windows, należy również wziąć pod uwagę przypadek, że żaden z nich nie jest zdefiniowany.

Ten temat obejmuje następujące procedury:

- [Korzystanie z biblioteki DLL systemu Win32 w aplikacji platformy uniwersalnej systemu](#BK_Win32DLL)

- [Korzystanie z natywnej biblioteki statycznej języka C++ w aplikacji platformy uniwersalnej systemu](#BK_StaticLib)

- [Przenoszenie biblioteki języka C++ do składnika środowiska wykonawczego systemu Windows](#BK_WinRTComponent)

## <a name="using-a-win32-dll-in-a-uwp-app"></a><a name="BK_Win32DLL"></a>Korzystanie z biblioteki DLL systemu Win32 w aplikacji platformy uniwersalnej systemu

Aby zapewnić większe bezpieczeństwo i niezawodność, uniwersalne aplikacje systemu Windows działają w ograniczonym środowisku wykonawczym, dzięki czemu nie można po prostu używać dowolnej natywnej biblioteki DLL w taki sposób, jak w klasycznej aplikacji klasycznej systemu Windows. Jeśli masz kod źródłowy dla biblioteki DLL, można przenieść kod tak, aby był uruchamiany na platformie uniwersalnej systemu ochrony systemu i platformy uniwersalnej systemu. Możesz zacząć od zmiany kilku ustawień projektu i metadanych pliku projektu, aby zidentyfikować projekt jako projekt platformy uniwersalnej systemu i platformy uniwersalnej systemu. Należy skompilować kod biblioteki przy użyciu `/ZW` opcji, która umożliwia C++/CX. Niektóre wywołania interfejsu API nie są dozwolone w aplikacjach platformy uniwersalnej systemu Windows ze względu na bardziej rygorystyczne kontrole skojarzone z tym środowiskiem. Zobacz [Interfejsy API win32 i COM dla aplikacji platformy uniwersalnej systemu Windows](/uwp/win32-and-com/win32-and-com-for-uwp-apps).

Poniższa procedura dotyczy przypadku, w którym masz natywną `__declspec(dllexport)`bibliotekę DLL, która udostępnia funkcje za pomocą .

### <a name="to-port-a-native-dll-to-the-uwp-without-creating-a-new-project"></a>Aby przenieść natywną bibliotekę DLL do platformy uniwersalnej systemu ochrony systemu ws.

1. Jeśli masz natywną bibliotekę `__declspec(dllexport)`DLL, która eksportuje funkcje przy użyciu , można wywołać te funkcje z aplikacji platformy uniwersalnej systemu Uniwersalnego, ponownie komponowanie biblioteki DLL jako projektu platformy uniwersalnej systemu. Załóżmy na przykład, że mamy bibliotekę DLL, która eksportuje kilka klas i ich metody, z kodem, takim jak następujący plik nagłówka:

    ```cpp
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

    ```cpp
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

   Wszystko inne w projekcie (stdafx.h, dllmain.cpp) jest częścią standardowego szablonu projektu Win32. Jeśli chcesz wykonać następujące czynności, ale nie chcesz jeszcze używać własnej biblioteki DLL z tymi krokami, spróbuj utworzyć projekt Win32, wybierz bibliotekę DLL w kreatorze projektu, a następnie dodaj plik nagłówka giraffe.h i plik kodu giraffe.cpp i skopiuj zawartość z kodu w tym kroku do odpowiednich plików.

   Kod definiuje makro, `GIRAFFE_API` które jest `__declspec(dllexport)` `_DLL` rozpoznawane, gdy jest zdefiniowany (to jest, gdy projekt jest zbudowany jako biblioteka DLL).

2. Otwórz **właściwości projektu** DLL i ustaw **konfigurację** na **Wszystkie konfiguracje**.

3. Na karcie **Właściwości projektu**w obszarze **C/C++** > **Ogólne** ustaw **opcję Zużywają rozszerzenie środowiska wykonawczego systemu Windows** na Tak **(/ZW).** Umożliwia to rozszerzenia komponentów (C++/CX).

4. W **Eksploratorze rozwiązań**wybierz węzeł projektu, otwórz menu skrótów i wybierz pozycję **Zwolnij projekt**. Następnie otwórz menu skrótów w niezaładowanym węźle projektu i wybierz opcję edycji pliku projektu. Zlokalizuj `WindowsTargetPlatformVersion` element i zastąp go następującymi elementami.

    ```xml
    <AppContainerApplication>true</AppContainerApplication>
    <ApplicationType>Windows Store</ApplicationType>
    <WindowsTargetPlatformVersion>10.0.10156.0</WindowsTargetPlatformVersion>
    <WindowsTargetPlatformMinVersion>10.0.10156.0</WindowsTargetPlatformMinVersion>
    <ApplicationTypeRevision>10.0</ApplicationTypeRevision>
    ```

   Zamknij plik .vcxproj, otwórz ponownie menu skrótów i wybierz polecenie **Załaduj ponownie program Project**.

   **Eksplorator rozwiązań** identyfikuje teraz projekt jako projekt systemu Uniwersalnego systemu Windows.

5. Upewnij się, że nazwa wstępnie skompilowanego pliku nagłówka jest poprawna. W sekcji **Wstępnie skompilowane nagłówki** zmień **wstępnie skompilowany plik nagłówka** z *pch.h* na *stdafx.h*. Jeśli tego nie zrobisz, zostanie wyświetlony następujący błąd.

   > błąd C2857: nie znaleziono instrukcji "#include" określonej za pomocą opcji wiersza polecenia /Ycpch.h w pliku źródłowym

   Problem polega na tym, że projekty systemu Uniwersalnego systemu Windows używają innej konwencji nazewnictwa dla wstępnie skompilowanego pliku nagłówka.

6. Skompiluj projekt. Mogą pojawić się błędy dotyczące niezgodnych opcji wiersza polecenia. Na przykład przestarzała, ale często używana opcja **Włącz minimalne przebudowy (/Gm)** jest domyślnie ustawiona `/ZW`w wielu starszych projektach C++ i jest niezgodna z programem .

   Niektóre funkcje nie są dostępne podczas kompilowania dla platformy uniwersalnego systemu Windows. Zostaną wyświetlene błędy kompilatora dotyczące wszelkich problemów. Zajmij się tymi problemami, dopóki nie będziesz mieć czystej kompilacji.

7. Aby użyć biblioteki DLL w aplikacji platformy uniwersalnej systemu Windows w tym samym rozwiązaniu, otwórz menu skrótów dla węzła projektu platformy uniwersalnej systemu Windows i wybierz pozycję **Dodaj** > **odwołanie**.

   W obszarze**Rozwiązanie** **projektów** > zaznacz pole wyboru obok projektu biblioteki DLL i wybierz przycisk **OK.**

8. Uwzględnij pliki nagłówkowe biblioteki w pliku *pch.h* aplikacji platformy uniwersalnej systemu Uniwersalnego.

    ```cpp
    #include "..\MyNativeDLL\giraffe.h"
    ```

9. Dodaj kod jak zwykle w projekcie platformy uniwersalnej systemu i platformy uniwersalnej systemu, aby wywołać funkcje i utworzyć typy z biblioteki DLL.

    ```cpp
    MainPage::MainPage()
    {
        InitializeComponent();
        GiraffeFactory gf;
        Giraffe* g = gf.Create();
        int id = g->GetID();
    }
    ```

## <a name="using-a-native-c-static-library-in-a-uwp-app"></a><a name="BK_StaticLib"></a>Korzystanie z natywnej biblioteki statycznej języka C++ w aplikacji platformy uniwersalnej systemu

Można użyć natywnej biblioteki statycznej języka C++ w projekcie platformy uniwersalnej systemu uniwersalnego, ale istnieją pewne ograniczenia i ograniczenia, o których należy pamiętać. Zacznij od przeczytania o [bibliotekach statycznych w języku C++/CX](../cppcx/static-libraries-c-cx.md). Dostęp do kodu macierzystego w bibliotece statycznej z aplikacji platformy uniwersalnej systemu uniwersalnego systemu nagłaśniać, ale nie jest zalecane tworzenie publicznych typów ref w takiej bibliotece statycznej. Jeśli skompilujesz bibliotekę `/ZW` statyczną z opcją, bibliotekarz (a właściwie konsolidator w przebraniu) ostrzega:

> LNK4264: archiwizacja pliku obiektu skompilowanego z /ZW do biblioteki statycznej; należy pamiętać, że podczas tworzenia typów środowiska wykonawczego systemu Windows nie zaleca się łączenia z biblioteką statyczną zawierającą metadane środowiska wykonawczego systemu Windows

Można jednak użyć biblioteki statycznej w platformie uniwersalnej `/ZW`systemu wyrozumiałej bez konieczności ponownego komppilowania jej za pomocą programu . Nie będzie można zadeklarować żadnych typów ref lub użyć konstrukcji C++/CX, ale jeśli twoim celem jest po prostu użyć biblioteki kodu macierzystego, a następnie można to zrobić, wykonując następujące kroki.

### <a name="to-use-a-native-c-static-library-in-a-uwp-project"></a>Aby użyć natywnej biblioteki statycznej języka C++ w projekcie platformy uniwersalnej systemu

1. We właściwościach projektu platformy uniwersalnej systemu uniwersalnego wybierz pozycję Wejście**konsolidatora** >  **Configuration Properties** > właściwości konfiguracji w lewym okienku.**Input** W prawym okienku dodaj ścieżkę do biblioteki we właściwości **Dodatkowe zależności.** Na przykład dla biblioteki w projekcie, która umieszcza swoje dane wyjściowe w *SolutionFolder*\Debug\MyNativeLibrary\MyNativeLibrary.lib, dodaj ścieżkę względną `Debug\MyNativeLibrary\MyNativeLibrary.lib`.

2. Dodaj instrukcję include, aby odwołać się do pliku nagłówka do pliku *pch.h* (jeśli jest obecny) lub w dowolnym pliku cpp w razie potrzeby, i zacznij dodawać kod, który używa biblioteki.

   ```cpp
   #include "..\MyNativeLibrary\giraffe.h"
   ```

   Nie należy dodawać odwołania w węźle **Odwołania** w **Eksploratorze rozwiązań**. Ten mechanizm działa tylko dla składników środowiska wykonawczego systemu Windows.

## <a name="porting-a-c-library-to-a-windows-runtime-component"></a><a name="BK_WinRTComponent"></a>Przenoszenie biblioteki języka C++ do składnika środowiska wykonawczego systemu Windows

Jeśli chcesz korzystać z natywnych interfejsów API w bibliotece statycznej z aplikacji platformy uniwersalnej systemu Windows i masz kod źródłowy biblioteki macierzystej, możesz przenieść kod do składnika środowiska wykonawczego systemu Windows. Nie będzie już biblioteki statycznej, będzie to biblioteka DLL. Można go używać w dowolnej aplikacji platformy uniwersalnej systemu i platformy uniwersalnej systemu i w języku angielskim, ale w przeciwieństwie do przypadku biblioteki statycznej, można dodać typy ref i inne konstrukcje C++/CX, które są dostępne dla klientów w dowolnym kodzie aplikacji platformy uniwersalnej systemu Uniwersalnego, niezależnie od języka. W związku z tym można uzyskać dostęp do tych typów z języka C#, Visual Basic lub JavaScript.  Podstawową procedurą jest utworzenie projektu składnika środowiska wykonawczego systemu Windows, skopiowanie kodu biblioteki statycznej do niego i rozwiązanie wszelkich `/ZW` błędów, które wynikają z przenoszenia kodu ze standardowej kompilacji języka C++ do kompilacji.

### <a name="to-port-a-c-library-to-a-windows-runtime-component"></a>Aby przenieść bibliotekę języka C++ do składnika środowiska wykonawczego systemu Windows

1. Utwórz projekt składnika środowiska wykonawczego systemu Windows.

2. Zamknij projekt.

3. W **Eksploratorze plików systemu Windows**znajdź projekt. Domyślnie program Visual Studio używa folderu Visual Studio 2017\Projects w folderze Dokumenty. Znajdź projekt biblioteki języka C++, który zawiera kod, który chcesz port. Skopiuj pliki źródłowe (pliki nagłówkowe, pliki kodu i inne zasoby, w tym w podkatalogach) z projektu biblioteki języka C++ i wklej je do folderu projektu, upewniając się, że zachowaj tę samą strukturę folderów.

4. Otwórz ponownie projekt składnika środowiska wykonawczego systemu Windows i otwórz menu skrótów dla węzła projektu w **Eksploratorze rozwiązań**i wybierz pozycję **Dodaj** > **istniejący element**.

5. Wybierz wszystkie pliki do dodania z oryginalnego projektu i wybierz przycisk **OK**. W razie potrzeby powtórzyć dla podfolderów.

6. Być może masz teraz zduplikowany kod. Jeśli masz więcej niż jeden wstępnie skompilowany nagłówek (powiedzmy *stdafx.h* i *pch.h),* wybierz jeden, aby zachować. Skopiuj dowolny wymagany kod, taki jak dołącz instrukcje, do tego, który przechowujesz. Następnie usuń inne i we właściwościach projektu w obszarze **Wstępnie skompilowane nagłówki**upewnij się, że nazwa pliku nagłówka jest poprawna.

   Jeśli plik ma być używany jako wstępnie skompilowany nagłówek, upewnij się, że wstępnie skompilowane opcje nagłówka są poprawne dla każdego pliku. Zaznacz każdy plik cpp po kolei, otwórz jego okno właściwości i upewnij się, że wszystkie są ustawione na **Use (/Yu),** z wyjątkiem żądanego wstępnie skompilowanego nagłówka, który powinien być ustawiony na **Utwórz (/Yc).**

7. Skompiluj projekt i rozwiąż wszelkie błędy. Te błędy mogą być spowodowane `/ZW` przy użyciu opcji lub mogą być spowodowane przez nową wersję zestawu Windows SDK lub mogą odzwierciedlać zależności, takie jak pliki nagłówkowe, od których zależy biblioteka, lub różnice w ustawieniach projektu między starym projektem a nowym.

8. Dodaj publiczne typy ref do projektu lub konwertuj zwykłe typy na typy ref, aby udostępnić punkty wejścia do funkcji, które chcesz wywołać z aplikacji platformy uniwersalnej systemu Windows.

9. Przetestuj składnik, dodając odwołanie do niego z projektu aplikacji platformy uniwersalnej systemu i dodaj kod, aby wywołać utworzone publiczne interfejsy API.

## <a name="see-also"></a>Zobacz też

[Przenoszenie na uniwersalną platformę systemu Windows](../porting/porting-to-the-universal-windows-platform-cpp.md)
