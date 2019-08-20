---
title: 'Instrukcje: Korzystanie z C++ istniejącego kodu w aplikacji platforma uniwersalna systemu Windows'
ms.date: 04/08/2019
ms.assetid: 87e5818c-3081-42f3-a30d-3dca2cf0645c
ms.openlocfilehash: 5050a9773eea55549958195efa624743f44ed031
ms.sourcegitcommit: 9d4ffb8e6e0d70520a1e1a77805785878d445b8a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/20/2019
ms.locfileid: "69630425"
---
# <a name="how-to-use-existing-c-code-in-a-universal-windows-platform-app"></a>Instrukcje: Korzystanie z C++ istniejącego kodu w aplikacji platforma uniwersalna systemu Windows

Prawdopodobnie najprostszym sposobem na rozpoczęcie pracy programu klasycznego w środowisku platforma uniwersalna systemu Windows (platformy UWP) jest użycie technologii mostka dla komputerów stacjonarnych. Obejmują one konwerter aplikacji klasycznych, który spowoduje spakowanie istniejącej aplikacji jako aplikacji platformy UWP bez konieczności wprowadzania zmian w kodzie. Aby uzyskać więcej informacji, zobacz [mostek Desktop](/windows/uwp/porting/desktop-to-uwp-root).

W pozostałej części tego tematu omówiono, C++ jak biblioteki portów (biblioteki DLL i biblioteki statyczne) do platforma uniwersalna systemu Windows. Można to zrobić, aby można było używać logiki podstawowej C++ z wieloma aplikacjami platformy UWP.

Aplikacje platformy UWP działają w chronionym środowisku, a w związku z tym wiele wywołań interfejsu API systemu Win32, COM i CRT, które mogą naruszać bezpieczeństwo platformy, nie są dozwolone. Kompilator może wykryć takie wywołania i wygenerować błąd, jeśli `/ZW` opcja jest używana. Możesz użyć zestawu certyfikacji aplikacji w swojej aplikacji, aby wykryć kod, który wywołuje zabronione interfejsy API. Aby uzyskać więcej informacji, zobacz [zestaw certyfikacji aplikacji systemu Windows](/windows/uwp/debug-test-perf/windows-app-certification-kit).

Jeśli dla biblioteki jest dostępny kod źródłowy, może być możliwe wyeliminowanie niedozwolonych wywołań interfejsu API. Aby uzyskać szczegółowe informacje, w tym listę interfejsów API, które są dozwolone lub zabronione, zobacz [interfejsy API Win32 i com dla aplikacji platformy UWP](/uwp/win32-and-com/win32-and-com-for-uwp-apps) i [funkcje CRT, które nie są obsługiwane w aplikacjach platforma uniwersalna systemu Windows](../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md). Niektóre alternatywy można znaleźć w temacie [alternatywy dla interfejsów API systemu Windows w aplikacjach platformy UWP](/uwp/win32-and-com/alternatives-to-windows-apis-uwp).

Jeśli po prostu próbujesz dodać odwołanie z uniwersalnego projektu systemu Windows do klasycznej biblioteki pulpitów, zostanie wyświetlony komunikat o błędzie informujący, że biblioteka nie jest zgodna. W przypadku biblioteki statycznej można utworzyć połączenie z biblioteką, po prostu dodając bibliotekę (plik. lib) do danych wejściowych konsolidatora, tak jak w klasycznej aplikacji Win32. W przypadku bibliotek, w których dostępny jest tylko plik binarny, jest to jedyna opcja. Biblioteka statyczna jest połączona z plikiem wykonywalnym aplikacji, ale biblioteka Win32 DLL, która jest zużywana w aplikacji platformy UWP, musi być pakowana do aplikacji, dołączając ją do projektu i oznaczyć jako zawartość. Aby załadować bibliotekę DLL Win32 w aplikacji platformy UWP, należy również wywołać [LoadPackagedLibrary](/windows/win32/api/winbase/nf-winbase-loadpackagedlibrary) zamiast `LoadLibrary` lub `LoadLibraryEx`.

Jeśli masz kod źródłowy biblioteki DLL lub statycznej, możesz ponownie skompilować `/ZW` program jako projekt platformy UWP. Jeśli to zrobisz, możesz dodać odwołanie przy użyciu **Eksplorator rozwiązań**i używać go w C++ aplikacjach platformy UWP. W przypadku biblioteki DLL można połączyć z biblioteką eksportu.

Aby uwidocznić funkcjonalność dla obiektów wywołujących w innych językach, można skonwertować bibliotekę na składnik środowisko wykonawcze systemu Windows. Składniki środowisko wykonawcze systemu Windows różnią się od zwykłych bibliotek DLL w tym, że zawierają metadane w postaci plików winmd, które opisują zawartość w sposób, w jaki użytkownicy platformy .NET i języka JavaScript potrzebują. Aby udostępnić elementy interfejsu API innym językom, można dodać C++konstrukcje/CX, takie jak klasy ref, i udostępnić je publicznie lub użyć [biblioteki szablonów środowisko wykonawcze systemu Windows C++ (WRL)](../windows/windows-runtime-cpp-template-library-wrl.md).  W systemie Windows 10 i nowszych można użyć [ C++biblioteki/WinRT](https://github.com/microsoft/cppwinrt) zamiast/CX. C++

Powyższa dyskusja nie dotyczy przypadku składników COM, które muszą być obsługiwane inaczej. Jeśli w pliku EXE lub DLL znajduje się serwer COM, można go użyć w uniwersalnym projekcie systemu Windows, o ile jest to pakiet jako [składnik COM bez rejestracji](/windows/win32/sbscs/creating-registration-free-com-objects), dodać go do projektu jako plik zawartości i utworzyć jego wystąpienie za pomocą [CoCreateInstanceFromApp](/windows/win32/api/combaseapi/nf-combaseapi-cocreateinstancefromapp). Aby uzyskać więcej informacji, zobacz [Używanie biblioteki DLL Free-com w C++ projekcie sklepu Windows](https://blogs.msdn.microsoft.com/win8devsupport/2013/05/19/using-free-com-dll-in-windows-store-c-project/).

Jeśli masz istniejącą bibliotekę COM, która ma zostać przeprowadzona do platformy UWP, możesz być w stanie skonwertować ją na składnik środowisko wykonawcze systemu Windows przy użyciu [biblioteki środowisko wykonawcze systemu Windows C++ Template Library (WRL)](../windows/windows-runtime-cpp-template-library-wrl.md). WRL nie obsługuje wszystkich funkcji ATL i OLE, więc czy taki port jest możliwy, zależy od tego, jak dużo kod COM zależy od tego, jakie funkcje COM, ATL i OLE wymaga składnik.

Są to różne sposoby używania istniejącego C++ kodu w projektach platformy UWP. Niektóre z tych metod nie wymagają ponownej kompilacji kodu z włączonymi rozszerzeniamiC++składnika (/CX) (to oznacza, że `/ZW` z opcją), a jeśli chcesz zachować kod w standardzie C++, lub zachować klasyczne środowisko kompilacji Win32 dla niektórych Możesz to zrobić, korzystając z odpowiednich opcji architektury. Na przykład, cały kod, który zawiera interfejs użytkownika platformy UWP i typy, które mają być uwidocznione C#, Visual Basic i obiekty wywołujące języka JavaScript powinny znajdować się w projektach aplikacji systemu Windows i środowisko wykonawcze systemu Windows projektach składników. Kod, który musi być używany tylko w C++ (w C++tym/CX), może znajdować się w projekcie, który jest kompilowany `/WX` przy użyciu opcji lub C++ projektu standardowego. Kod tylko binarny może być używany przez połączenie go jako Biblioteka statyczna lub spakowany z aplikacją jako zawartość i załadowana do biblioteki DLL tylko wtedy, gdy nie korzysta z niedozwolonych interfejsów API.

Niezależnie od tego, który z tych scenariuszy programistycznych jest wybierany, należy pamiętać o kilku definicjach makr, których można użyć w kodzie, aby można było kompilować kod warunkowo w klasycznym środowisku Win32 i platformy UWP.

```cpp
#if WINAPI_FAMILY_PARTITION(WINAPI_PARTITION_PC_APP)
#if WINAPI_FAMILY_PARTITION(WINAPI_PARTITION_PHONE_APP)
#if WINAPI_FAMILY_PARTITION(WINAPI_PARTITION_APP)
#if WINAPI_FAMILY_PARTITION(WINAPI_PARTITION_DESKTOP)
```

Te instrukcje dotyczą odpowiednio aplikacji platformy UWP, aplikacji ze sklepu Windows Phone, obu lub nie (tylko klasyczny pulpit Win32). Te makra są dostępne tylko w Windows SDK 8,1 i nowszych, więc jeśli kod wymaga skompilowania ze starszymi wersjami Windows SDK lub dla innych platform oprócz systemu Windows, należy rozważyć również przypadek, w którym żaden z nich nie jest zdefiniowany.

Ten temat obejmuje następujące procedury:

- [Korzystanie z biblioteki Win32 DLL w aplikacji platformy UWP](#BK_Win32DLL)

- [Używanie natywnej C++ biblioteki statycznej w aplikacji platformy UWP](#BK_StaticLib)

- [Przenoszenie C++ biblioteki do składnika Środowisko wykonawcze systemu windowsowego](#BK_WinRTComponent)

##  <a name="BK_Win32DLL"></a>Korzystanie z biblioteki Win32 DLL w aplikacji platformy UWP

Aby zapewnić lepsze zabezpieczenia i niezawodność, aplikacje uniwersalne systemu Windows działają w ograniczonym środowisku wykonawczym, więc nie można używać żadnej natywnej biblioteki DLL w sposób klasyczny w klasycznej aplikacji klasycznej systemu Windows. Jeśli masz kod źródłowy dla biblioteki DLL, możesz przenieść kod tak, aby był on uruchamiany w platformy UWP. Zacznij od zmiany kilku ustawień projektu i metadanych pliku projektu, aby zidentyfikować projekt jako projekt platformy UWP. Należy skompilować kod biblioteki przy użyciu `/ZW` opcji, która umożliwia/CX. C++ Niektóre wywołania interfejsu API są niedozwolone w aplikacjach platformy UWP ze względu na bardziej rygorystyczne kontrolki skojarzone z tym środowiskiem. Zobacz [interfejsy API Win32 i com dla aplikacji platformy UWP](/uwp/win32-and-com/win32-and-com-for-uwp-apps).

Poniższa procedura dotyczy przypadku, w którym masz natywną bibliotekę DLL, która uwidacznia funkcje `__declspec(dllexport)`przy użyciu.

### <a name="to-port-a-native-dll-to-the-uwp-without-creating-a-new-project"></a>Aby przenieść natywną bibliotekę DLL do platformy UWP bez tworzenia nowego projektu

1. Jeśli masz natywną bibliotekę DLL, która eksportuje funkcje `__declspec(dllexport)`przy użyciu, możesz wywołać te funkcje z poziomu aplikacji platformy UWP przez ponowną kompilację biblioteki DLL jako projektu platformy UWP. Załóżmy na przykład, że mamy bibliotekę DLL, która eksportuje kilka klas i ich metod, przy użyciu kodu, takiego jak następujący plik nagłówkowy:

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

   Wszystkie inne elementy w projekcie (stdafx. h, DllMain. cpp) są częścią standardowego szablonu projektu środowiska Win32. Jeśli chcesz wykonać tę procedurę, ale nie chcesz używać własnej biblioteki DLL jeszcze z tymi krokami, spróbuj utworzyć projekt Win32, wybierz pozycję DLL w Kreatorze projektu, a następnie Dodaj plik nagłówka Giraffe. h i plik kodu Giraffe. cpp i skopiuj zawartość kodu z tego kroku do aplikacji Pliki ropriate.

   Kod definiuje makro `GIRAFFE_API` , które jest `__declspec(dllexport)` rozpoznawane jako `_DLL` , gdy jest zdefiniowane (to jest, gdy projekt jest skompilowany jako biblioteka DLL).

2. Otwórz **właściwości projektu** dla projektu DLL i ustaw **konfigurację** na **wszystkie konfiguracje**.

3. We **właściwościach projektu**na karcie **C/C++**  > **Ogólne** ustaw wartość Użyj **środowisko wykonawcze systemu Windows Extension** na **wartość tak (/zw)** . Spowoduje to włączenie rozszerzeń składnikówC++(/CX).

4. W **Eksplorator rozwiązań**wybierz węzeł projektu, otwórz menu skrótów i wybierz polecenie Zwolnij **projekt**. Następnie otwórz menu skrótów w węźle niezaładowanego projektu, a następnie wybierz polecenie Edytuj plik projektu. `WindowsTargetPlatformVersion` Znajdź element i zastąp go następującymi elementami.

    ```xml
    <AppContainerApplication>true</AppContainerApplication>
    <ApplicationType>Windows Store</ApplicationType>
    <WindowsTargetPlatformVersion>10.0.10156.0</WindowsTargetPlatformVersion>
    <WindowsTargetPlatformMinVersion>10.0.10156.0</WindowsTargetPlatformMinVersion>
    <ApplicationTypeRevision>10.0</ApplicationTypeRevision>
    ```

   Zamknij plik. vcxproj, Otwórz ponownie menu skrótów i wybierz polecenie **Załaduj ponownie projekt**.

   **Eksplorator rozwiązań** teraz identyfikuje projekt jako uniwersalny projekt systemu Windows.

5. Upewnij się, że nazwa pliku prekompilowanego nagłówka jest poprawna. W sekcji **prekompilowane nagłówki** Zmień **wstępnie skompilowany plik nagłówkowy** z *PCH. h* na *stdafx. h*. Jeśli tego nie zrobisz, zostanie wyświetlony następujący błąd.

   > błąd C2857: Instrukcja "#include" określona za pomocą/Ycpch.h opcji wiersza polecenia nie została znaleziona w pliku źródłowym

   Problem polega na tym, że uniwersalne projekty systemu Windows używają innej konwencji nazewnictwa dla prekompilowanego pliku nagłówkowego.

6. Skompiluj projekt. Mogą wystąpić błędy dotyczące niezgodnych opcji wiersza polecenia. Na przykład obecnie przestarzałe, ale często używane opcje Włącz minimalną ponowną kompilację **(/GM)** jest domyślnie ustawiona w C++ wielu starszych projektach i jest niezgodna z `/ZW`.

   Niektóre funkcje nie są dostępne podczas kompilowania dla platforma uniwersalna systemu Windows. Zostaną wyświetlone błędy kompilatora dotyczące wszelkich problemów. Należy je rozwiązać, dopóki nie zostanie wyczyszczona.

7. Aby użyć biblioteki DLL w aplikacji platformy UWP w tym samym rozwiązaniu, otwórz menu skrótów dla węzła projektu platformy UWP i wybierz polecenie **Dodaj** > **odwołanie**.

   W obszarze **projekty** > **rozwiązania**zaznacz pole wyboru obok projektu DLL, a następnie wybierz przycisk **OK** .

8. Uwzględnij pliki nagłówkowe biblioteki w pliku *PCH. h* aplikacji platformy UWP.

    ```cpp
    #include "..\MyNativeDLL\giraffe.h"
    ```

9. Dodaj kod w zwykły sposób w projekcie platformy UWP, aby wywoływać funkcje i tworzyć typy z biblioteki DLL.

    ```cpp
    MainPage::MainPage()
    {
        InitializeComponent();
        GiraffeFactory gf;
        Giraffe* g = gf.Create();
        int id = g->GetID();
    }
    ```

##  <a name="BK_StaticLib"></a>Używanie natywnej C++ biblioteki statycznej w aplikacji platformy UWP

Można użyć natywnej C++ biblioteki statycznej w projekcie platformy UWP, ale istnieją pewne ograniczenia i ograniczenia, które należy znać. Zacznij od odczytywania [bibliotek statycznych w C++/CX](../cppcx/static-libraries-c-cx.md). Możesz uzyskać dostęp do kodu natywnego w bibliotece statycznej z aplikacji platformy UWP, ale nie zaleca się tworzenia publicznych typów referencyjnych w takiej bibliotece statycznej. W przypadku kompilowania biblioteki statycznej z `/ZW` opcją bibliotekarza (w rzeczywistości konsolidator w przebraniu) ostrzega:

> LNK4264: archiwizowanie pliku obiektu skompilowanego z/ZW w bibliotece statycznej; należy pamiętać, że podczas tworzenia typów środowisko wykonawcze systemu Windows nie zaleca się łączenia z biblioteką statyczną zawierającą środowisko wykonawcze systemu Windows metadanych

Można jednak użyć biblioteki statycznej w platformy UWP bez ponownego kompilowania jej w programie `/ZW`. Nie będzie można zadeklarować żadnych typów referencyjnych ani używać C++konstrukcji/CX, ale jeśli chcesz po prostu użyć biblioteki kodu natywnego, możesz to zrobić, wykonując następujące kroki.

### <a name="to-use-a-native-c-static-library-in-a-uwp-project"></a>Aby użyć natywnej C++ biblioteki statycznej w projekcie platformy UWP

1. We właściwościach projektu dla projektu platformy UWP wybierz pozycję **Właściwości** > konfiguracji**dane wejściowe** **konsolidatora** > w okienku po lewej stronie. W okienku po prawej stronie Dodaj ścieżkę do biblioteki we właściwości **dodatkowe zależności** . Na przykład dla biblioteki w projekcie, która umieszcza dane wyjściowe w *SolutionFolder*\Debug\MyNativeLibrary\MyNativeLibrary.lib, Dodaj ścieżkę `Debug\MyNativeLibrary\MyNativeLibrary.lib`względną.

2. Dodaj instrukcję include, aby odwoływać się do pliku nagłówkowego w pliku *PCH. h* (jeśli istnieje) lub w dowolnym pliku. cpp w razie potrzeby, a następnie zacznij dodawać kod, który używa biblioteki.

   ```cpp
   #include "..\MyNativeLibrary\giraffe.h"
   ```

   Nie dodawaj odwołania w węźle **References** w **Eksplorator rozwiązań**. Ten mechanizm działa tylko w przypadku składników środowisko wykonawcze systemu Windows.

##  <a name="BK_WinRTComponent"></a>Przenoszenie C++ biblioteki do składnika Środowisko wykonawcze systemu windowsowego

Jeśli chcesz korzystać z natywnych interfejsów API w bibliotece statycznej z poziomu aplikacji platformy UWP i masz kod źródłowy biblioteki natywnej, możesz przenieść kod do składnika środowisko wykonawcze systemu Windows. Nie jest już biblioteką statyczną, będzie to biblioteka DLL. Możesz użyć jej w dowolnej C++ aplikacji platformy UWP, ale w przeciwieństwie do przypadku biblioteki statycznej można dodać typy referencyjne i inne C++konstrukcje/CX, które są dostępne dla klientów w dowolnym kodzie aplikacji platformy UWP, niezależnie od języka. W związku z tym możesz uzyskać dostęp do C#tych typów z, Visual Basic lub JavaScript.  Podstawowa procedura polega na utworzeniu projektu składnika Środowisko wykonawcze systemu Windows, skopiowaniu kodu biblioteki statycznej do niego i rozwodzeniu wszelkich błędów, które wynikają z przeniesienia kodu z standardowej C++ kompilacji do `/ZW` kompilacji.

### <a name="to-port-a-c-library-to-a-windows-runtime-component"></a>Aby przenieść C++ bibliotekę do składnika Środowisko wykonawcze systemu Windows

1. Utwórz projekt składnika środowisko wykonawcze systemu Windows.

2. Zamknij projekt.

3. Zlokalizuj projekt w **Eksploratorze plików systemu Windows**. Domyślnie program Visual Studio używa folderu programu Visual Studio 2017 \ projects w folderze Documents. Znajdź projekt C++ biblioteki zawierający kod, który chcesz przenieść. Skopiuj pliki źródłowe (pliki nagłówkowe, pliki kodu i inne zasoby, w tym w podkatalogach) z projektu C++ biblioteki i wklej je do folderu projektu, aby zachować tę samą strukturę folderów.

4. Otwórz ponownie projekt składnika Środowisko wykonawcze systemu Windows, a następnie otwórz menu skrótów dla węzła projektu w **Eksplorator rozwiązań**i wybierz polecenie **Dodaj** > **istniejący element**.

5. Zaznacz wszystkie pliki, które mają zostać dodane z oryginalnego projektu, a następnie wybierz **przycisk OK**. Powtórz w razie potrzeby dla podfolderów.

6. Może teraz istnieć pewien duplikat kodu. Jeśli masz więcej niż jeden prekompilowany nagłówek (Powiedz *stdafx. h* i *PCH. h*), wybierz jedną, która ma zostać zachowana. Skopiuj dowolny wymagany kod, taki jak instrukcje include, do tej, która jest zachowywana. Następnie usuń inne i we właściwościach projektu w obszarze prekompilowane **nagłówki**upewnij się, że nazwa pliku nagłówka jest poprawna.

   Jeśli plik został zmieniony tak, aby używał jako prekompilowanego nagłówka, upewnij się, że opcje prekompilowanego nagłówka są poprawne dla każdego pliku. Zaznacz każdy plik CPP z kolei, otwórz jego okno właściwości i upewnij się, że wszystkie są ustawione na **Użyj (/Yu)** , z wyjątkiem żądanego prekompilowanego nagłówka, który powinien być ustawiony na **Utwórz (/Yc)** .

7. Skompiluj projekt i Usuń wszelkie błędy. Te błędy mogą być spowodowane użyciem `/ZW` opcji lub mogą być spowodowane przez nową wersję Windows SDK lub mogą odzwierciedlać zależności, takie jak pliki nagłówkowe, od których zależy Twoja biblioteka, lub różnice w ustawieniach projektu między Starym projekt i nowy.

8. Dodaj publiczne typy odwołań do projektu lub przekonwertuj zwykłe typy na typy referencyjne, aby uwidocznić punkty wejścia do funkcji, które mają być wywoływane z aplikacji platformy UWP.

9. Przetestuj składnik, dodając odwołanie do niego z projektu aplikacji platformy UWP i dodając kod do wywoływania publicznych interfejsów API, które zostały utworzone.

## <a name="see-also"></a>Zobacz także

[Przenoszenie do platforma uniwersalna systemu Windows](../porting/porting-to-the-universal-windows-platform-cpp.md)
