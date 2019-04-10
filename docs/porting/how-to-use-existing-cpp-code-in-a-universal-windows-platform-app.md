---
title: 'Instrukcje: Używanie istniejącego kodu C++ w aplikacji platformy uniwersalnej Windows'
ms.date: 04/08/2019
ms.assetid: 87e5818c-3081-42f3-a30d-3dca2cf0645c
ms.openlocfilehash: 3aeef205effe072a25fc0b3dabb9145245461d45
ms.sourcegitcommit: 39debf8c525c3951af6913ee5e514617658f8859
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59424199"
---
# <a name="how-to-use-existing-c-code-in-a-universal-windows-platform-app"></a>Instrukcje: Używanie istniejącego kodu C++ w aplikacji platformy uniwersalnej Windows

Najprostszym sposobem programu desktop działające w środowisku Windows platformy Uniwersalnej jest prawdopodobnie używać technologii Desktop Bridge. Obejmują one Desktop App Converter, która będzie spakować swoją istniejącą aplikację jako aplikację platformy uniwersalnej systemu Windows bez wymaganych zmian w kodzie. Aby uzyskać więcej informacji, zobacz [Desktop Bridge](/windows/uwp/porting/desktop-to-uwp-root).

Pozostała część tego tematu opisano kroki umożliwiające portu C++ biblioteki (dll i bibliotek statycznych) do uniwersalnej platformy Windows. Można to zrobić, tak aby podstawowych logiki C++ mogą być używane z wieloma aplikacjami platformy uniwersalnej systemu Windows.

Aplikacje platformy uniwersalnej systemu Windows jest uruchomiona w środowisku chronionego, a w rezultacie wiele wywołań Win32 i COM, CRT API, które mogą negatywnie wpłynąć na bezpieczeństwo platformy nie są dozwolone. Kompilator może wykryć takie połączenia i generuje błąd, w przypadku `/ZW` jest używana opcja. Zestaw certyfikacji aplikacji dla aplikacji służy do wykrywania kodu, który wywołuje interfejsy API zabronione. Aby uzyskać więcej informacji, zobacz [zestawu certyfikacji aplikacji Windows](/windows/uwp/debug-test-perf/windows-app-certification-kit).

Kod źródłowy jest dostępny dla biblioteki, można wyeliminować zabronione wywołań interfejsu API. Aby uzyskać szczegółowe informacje, łącznie z listą interfejsów API, które są dozwolone lub zabronione, zobacz [Win32 i interfejsów API modelu COM dla aplikacji platformy UWP](/uwp/win32-and-com/win32-and-com-for-uwp-apps) i [funkcje CRT nieobsługiwane w aplikacjach platformy uniwersalnej Windows](../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md). Kilka alternatyw znajduje się w temacie [alternatywy dla Windows API w aplikacjach platformy UWP](/uwp/win32-and-com/alternatives-to-windows-apis-uwp).

Jeśli spróbujesz dodać odwołanie z projektu Windows Universal do klasycznego biblioteki pulpitu, otrzymasz komunikat o błędzie stwierdzający, że biblioteka nie jest zgodny. W przypadku biblioteki statycznej możesz połączyć do biblioteki przez dodanie biblioteki (plik .lib) na dane wejściowe konsolidatora, tak samo jak w aplikacji klasycznej Win32. W przypadku bibliotek, gdzie dostępna jest tylko plik binarny jest jedyną opcją. Biblioteka statyczna jest połączony plik wykonywalny aplikacji, ale DLL Win32, którą możesz wykorzystać w aplikacji platformy uniwersalnej systemu Windows muszą być spakowane w aplikacji, dołączając ją w projekcie i oznaczenie jej jako zawartości. Aby załadować bibliotekę DLL Win32 w aplikacji platformy uniwersalnej systemu Windows, musisz też wywołać [LoadPackagedLibrary](/windows/desktop/api/winbase/nf-winbase-loadpackagedlibrary) zamiast `LoadLibrary` lub `LoadLibraryEx`.

Jeśli masz kod źródłowy dla biblioteki DLL lub biblioteki statycznej, można ponownie skompilować z `/ZW` jako projekt platformy uniwersalnej systemu Windows. Jeśli to zrobisz, można dodać odwołania za pomocą **Eksploratora rozwiązań**i używać go w aplikacji platformy UWP w języku C++. W przypadku biblioteki DLL możesz połączyć się z biblioteką eksportu.

Aby udostępnić funkcje dotyczące obiektów wywołujących w innych językach, biblioteki można przekonwertować na składnik środowiska wykonawczego Windows. Składniki środowiska uruchomieniowego Windows różnią się od zwykłych bibliotek DLL obejmują one metadanych w formie plików winmd, które opisują zawartości w taki sposób, aby wymagać konsumentów platformy .NET i języka JavaScript. Aby udostępnić elementów interfejsu API do innych języków, możesz dodać C++/CX konstrukcji, takich jak klasy ref i zmień je na publiczną lub użyj [Windows Runtime C++ szablon biblioteki (WRL)](../windows/windows-runtime-cpp-template-library-wrl.md).  W systemie Windows 10 i nowszych możesz użyć [ C++biblioteki /WinRT](https://github.com/microsoft/cppwinrt) zamiast C++/CX.

Poprzedni dyskusji nie ma zastosowania do przypadku składników modelu COM, które muszą być obsługiwane inaczej. Jeśli masz serwer COM, EXE lub DLL, służy w projekcie Windows Universal tak długo, jak go jako pakietu [bez rejestracji składników COM](/windows/desktop/sbscs/creating-registration-free-com-objects), dodaj go do projektu, jak i zawartości pliku i za pomocą wystąpienia [ CoCreateInstanceFromApp](/windows/desktop/api/combaseapi/nf-combaseapi-cocreateinstancefromapp). Aby uzyskać więcej informacji, zobacz [przy użyciu biblioteki DLL modelu COM bezpłatna w projekcie programu Windows Store języka C++](https://blogs.msdn.microsoft.com/win8devsupport/2013/05/19/using-free-com-dll-in-windows-store-c-project/).

Jeśli masz istniejącej biblioteki COM, które chcesz przenieść do platformy uniwersalnej systemu Windows, można go przekonwertować na składnik środowiska wykonawczego Windows za pomocą [Windows środowiska uruchomieniowego C++ szablon biblioteki (WRL)](../windows/windows-runtime-cpp-template-library-wrl.md). WRL nie obsługuje wszystkie funkcje biblioteki ATL i OLE, więc tego, czy jest możliwe takiego portu zależy od ilości kodu COM jest zależna od jakie funkcje COM, ATL, i OLE składnika wymaga.

Są to różne sposoby, w projektach platformy uniwersalnej systemu Windows, można użyć istniejącego kodu C++. Niektóre sposoby nie wymagają kodu do ponownej kompilacji przy użyciu rozszerzeń składnika (C++/CX) włączone (oznacza to, za pomocą `/ZW` opcja), i niektóre wykonania, tak aby w przypadku należy zachować kod w standardzie C++, lub zachować klasyczne środowisko kompilacji Win32 dla niektórych Kod, możesz to zrobić, z opcjami odpowiednią architekturę. Na przykład kodu, który zawiera interfejs użytkownika platformy uniwersalnej systemu Windows i typy, które mają być udostępniana dla obiektów wywołujących C#, Visual Basic i języka JavaScript należy się w aplikacji Windows i składnika środowiska wykonawczego Windows projektów. Kod, który ma być używane tylko w C++ (w tym C++/CX) kod może być w projekcie, który kompiluje z `/WX` opcji lub standardowego C++ projektu. Tylko do pliku binarnego kod może być używany, łącząc je w jako bibliotekę statyczną lub za pomocą aplikacji jako zawartości w pakiecie i załadowany w bibliotece DLL, tylko wtedy, gdy nie korzysta się z niedozwolonych interfejsów API.

Niezależnie od tego, który z tych scenariuszy programowania wybierzesz których trzeba wiedzieć liczby definicji makra, które można użyć w kodzie, dzięki czemu można kompilować kod warunkowo w ramach klasycznej Win32 pulpitu i platformy uniwersalnej systemu Windows.

```cpp
#if WINAPI_FAMILY_PARTITION(WINAPI_PARTITION_PC_APP)
#if WINAPI_FAMILY_PARTITION(WINAPI_PARTITION_PHONE_APP)
#if WINAPI_FAMILY_PARTITION(WINAPI_PARTITION_APP)
#if WINAPI_FAMILY_PARTITION(WINAPI_PARTITION_DESKTOP)
```

Te instrukcje odpowiednio mają zastosowanie do aplikacji platformy UWP, Windows Phone Store aplikacji, zarówno lub żadna (klasycznej Win32 tylko dla komputerów stacjonarnych). Te makra są dostępne tylko w Windows SDK 8.1 i nowszych wersjach, więc jeśli kod musi mieć formę skompilowaną przy użyciu wcześniejszych wersji zestawu Windows SDK lub dla innych platform, oprócz Windows, a następnie należy również rozważyć, tak że żaden z nich są zdefiniowane.

Ten temat obejmuje następujące procedury:

- [Za pomocą systemu Win32 DLL w aplikacji platformy uniwersalnej systemu Windows](#BK_Win32DLL)

- [Za pomocą natywną bibliotekę statyczną C++ w aplikacji platformy uniwersalnej systemu Windows](#BK_StaticLib)

- [Przenoszenie biblioteki języka C++ do składnika środowiska wykonawczego Windows](#BK_WinRTComponent)

##  <a name="BK_Win32DLL"></a> Za pomocą systemu Win32 DLL w aplikacji platformy uniwersalnej systemu Windows

Dla lepsze bezpieczeństwo i niezawodność Universal Windows Apps działają w środowisku ograniczony w czasie wykonywania, więc nie można po prostu użyć dowolnego natywnej biblioteki DLL sposób, jak w klasycznej aplikacji pulpitu Windows. Jeśli masz kod źródłowy dla biblioteki DLL mogą przeniesiesz kod tak, aby była uruchamiana na platformy uniwersalnej systemu Windows. Należy najpierw zmienić kilka ustawień projektu i metadane pliku projektu do identyfikowania projektu jako projektu platformy uniwersalnej systemu Windows. Należy przeprowadzić kompilowanie przy użyciu kodu biblioteki `/ZW` opcji, co pozwoli C++/CX. Niektóre wywołania interfejsu API nie są dozwolone w aplikacjach platformy uniwersalnej systemu Windows ze względu na bardziej restrykcyjne kontrolki skojarzone z tym środowisku. Zobacz [Win32 i interfejsów API modelu COM dla aplikacji platformy UWP](/uwp/win32-and-com/win32-and-com-for-uwp-apps).

Poniższa procedura ma zastosowanie w przypadku których masz natywnej biblioteki DLL, która udostępnia funkcje przy użyciu `__declspec(dllexport)`.

### <a name="to-port-a-native-dll-to-the-uwp-without-creating-a-new-project"></a>Port natywnej biblioteki DLL do platformy uniwersalnej systemu Windows bez tworzenia nowego projektu

1. Jeśli masz natywnej biblioteki DLL, które eksportuje funkcje za pomocą `__declspec(dllexport)`, te funkcje można wywołać z aplikacji platformy uniwersalnej systemu Windows, przez kompilację DLL jako projekt platformy uniwersalnej systemu Windows. Na przykład załóżmy, że mamy biblioteki DLL, które eksportuje kilka klas i metod ich przy użyciu kodu, takich jak poniższym pliku nagłówka:

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

   I następującego pliku kodu:

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

   Wszystko inne w projekcie (pliku stdafx.h, dllmain.cpp) jest częścią standardowego szablonu projektu Win32. Jeśli chcesz z niego skorzystać, ale nie chcesz używać własnych bibliotek DLL jeszcze za pomocą tych kroków, spróbuj utworzyć projekt systemu Win32, wybierz plik DLL w Kreatorze projektu następnie Dodaj nagłówek pliku giraffe.h i kod pliku giraffe.cpp i skopiuj zawartość z kodu w tym kroku do aplikacji pliki ropriate.

   Ten kod definiuje makro `GIRAFFE_API` która jest rozpoznawana jako `__declspec(dllexport)` podczas `_DLL` zdefiniowano (to znaczy, gdy projekt jest kompilowany jako biblioteka DLL).

2. Otwórz **właściwości projektu** projekt DLL i zestaw **konfiguracji** do **wszystkie konfiguracje**.

3. W **właściwości projektu**w obszarze **C/C++** > **ogólne** kartę, należy ustawić **używanie rozszerzenia środowiska uruchomieniowego Windows** do  **Tak (/ZW)**. Dzięki temu rozszerzenia składnika (C++/CX).

4. W **Eksploratora rozwiązań**, wybierz węzeł projektu, otwórz menu skrótów i wybierz **Zwolnij projekt**. Następnie otwórz menu skrótów w węźle zwolnionego projektu, a następnie wybrać opcję Edytuj plik projektu. Znajdź `WindowsTargetPlatformVersion` elementu i Zastąp następujące elementy.

    ```xml
    <AppContainerApplication>true</AppContainerApplication>
    <ApplicationType>Windows Store</ApplicationType>
    <WindowsTargetPlatformVersion>10.0.10156.0</WindowsTargetPlatformVersion>
    <WindowsTargetPlatformMinVersion>10.0.10156.0</WindowsTargetPlatformMinVersion>
    <ApplicationTypeRevision>10.0</ApplicationTypeRevision>
    ```

   Zamknij plik .vcxproj, ponownie otwórz menu skrótów i wybierz **Załaduj ponownie projekt**.

   **Eksplorator rozwiązań** identyfikuje projektu jako projektu Universal Windows.

5. Upewnij się, że nazwy pliku prekompilowanego pliku nagłówkowego jest poprawna. W **prekompilowanych nagłówków** sekcji, zmień **Prekompilowanego pliku nagłówkowego** z pch.h do stdafx.h. Jeśli tego nie zrobisz, zostanie wyświetlony następujący błąd.

   > Błąd C2857: "#include" nie można odnaleźć instrukcja określony za pomocą opcji wiersza polecenia /Ycpch.h w pliku źródłowym

   Problem polega na tym, że projektów Windows Universal używać różnych konwencji nazewnictwa dla prekompilowanego pliku nagłówkowego.

6. Skompiluj projekt. Możesz otrzymać błędy dotyczące opcje niezgodne wiersza polecenia. Na przykład opcja teraz przestarzałe, ale często używanych **Włącz minimalną ponowną kompilację (/ Gm)** jest ustawiana domyślnie wielu starszych C++ projektów i jest niezgodny z `/ZW`.

   Niektóre funkcje nie są dostępne podczas kompilowania dla platformy uniwersalnej Windows. Błędy kompilatora dotyczące wszystkich problemów zostanie wyświetlony. Ich rozwiązywania przy użyciu aż do uzyskania czysta kompilacja.

7. Aby korzystać z biblioteki DLL w aplikacji platformy uniwersalnej systemu Windows, w tym samym rozwiązaniu, otwórz menu skrótów dla węzła projektu platformy uniwersalnej systemu Windows, a następnie wybierz **Dodaj** > **odwołania**.

   W obszarze **projektów** > **rozwiązania**, zaznacz pole wyboru obok projektu biblioteki DLL, a wybierz **OK** przycisku.

8. Uwzględnij biblioteki, pliki nagłówka w pliku pch.h aplikacji platformy uniwersalnej systemu Windows.

    ```cpp
    #include "..\MyNativeDLL\giraffe.h"
    ```

9. Dodaj kod, jak zwykle w projekcie platformy uniwersalnej systemu Windows, aby wywoływać funkcje i tworzenie typów z biblioteki DLL.

    ```cpp
    MainPage::MainPage()
    {
        InitializeComponent();
        GiraffeFactory gf;
        Giraffe* g = gf.Create();
        int id = g->GetID();
    }
    ```

##  <a name="BK_StaticLib"></a> Za pomocą natywną bibliotekę statyczną C++ w aplikacji platformy uniwersalnej systemu Windows

Można użyć natywną bibliotekę statyczną C++ w projektach platformy uniwersalnej systemu Windows, ale istnieją pewne ograniczenia i ograniczenia wiedzieć. Rozpocznij, czytając o [bibliotek statycznych w C++/CX](../cppcx/static-libraries-c-cx.md). Możesz uzyskać dostęp kodu natywnego w bibliotece statycznej z aplikacji platformy uniwersalnej systemu Windows, ale nie zaleca się tworzenie typów publicznych ref w bibliotece statycznej. Jeśli kompilujesz z biblioteki statycznej `/ZW` opcję ostrzega bibliotekarza (faktycznie konsolidator kamuflażu):

> LNK4264: archiwizowanie pliku obiektu skompilowanego z parametrem /ZW do biblioteki statycznej; należy pamiętać, że podczas tworzenia typów środowiska wykonawczego Windows nie zaleca się połączyć z biblioteką statyczną zawierającą metadane środowiska wykonawczego Windows

Jednak można użyć biblioteki statycznej w platformy uniwersalnej systemu Windows bez konieczności ponownego kompilowania za pomocą `/ZW`. Nie można zadeklarować wszelkie typy ref lub użyć C++/CX konstrukcji, ale jeśli Twoja ma na celu po prostu użyć biblioteki kodu natywnego, a następnie możesz to zrobić, wykonując następujące kroki.

### <a name="to-use-a-native-c-static-library-in-a-uwp-project"></a>Aby użyć natywną bibliotekę statyczną C++ w projektach platformy uniwersalnej systemu Windows

1. We właściwościach projektu dla projektu platformy UWP w **konsolidatora** sekcji, Dodaj ścieżkę do biblioteki w **dane wejściowe** właściwości. Na przykład dla biblioteki w projekcie, która umieszcza dane wyjściowe w *SolutionFolder*\Debug\MyNativeLibrary\MyNativeLibrary.lib, Dodaj ścieżkę względną `Debug\MyNativeLibrary\MyNativeLibrary.lib`.

2. Dodaj instrukcję include, aby odwoływać się do pliku nagłówka do Twojej pch.h w projekcie platformy uniwersalnej systemu Windows i zacznij dodawać kod, który korzysta z biblioteki.

   ```cpp
   #include "..\MyNativeLibrary\giraffe.h"
   ```

   Nie należy dodawać odwołań w **odwołania** w węźle **Eksploratora rozwiązań**. Mechanizm ten działa tylko dla składników środowiska wykonawczego Windows.

##  <a name="BK_WinRTComponent"></a> Przenoszenie biblioteki języka C++ do składnika środowiska wykonawczego Windows

Jeśli chcesz korzystać z natywnych interfejsów API w bibliotece statycznej w aplikacji platformy uniwersalnej systemu Windows, a masz kod źródłowy dla natywnej biblioteki, można przenosić kod do składnika środowiska wykonawczego Windows. Nie będzie już bibliotekę statyczną, będzie on biblioteki DLL. Można w dowolnym C++ aplikacji platformy uniwersalnej systemu Windows, ale inaczej niż w przypadku biblioteki statycznej, można dodać typach ref i inne C++/CX konstrukcji, które są dostępne dla klientów w kodzie do aplikacji platformy uniwersalnej systemu Windows, niezależnie od języka. W związku z tym są dostępne następujące typy języka C#, Visual Basic lub JavaScript.  Podstawowa procedura polega na Utwórz projekt składnika środowiska wykonawczego Windows, skopiuj kod biblioteki statycznej do niego i rozwiązać wszelkie błędy, które wynikają z przenoszenia kodu z standardowa kompilacji C++ `/ZW` kompilacji.

### <a name="to-port-a-c-library-to-a-windows-runtime-component"></a>Do portu bibliotekę języka C++ do składnika środowiska wykonawczego Windows

1. Utwórz projekt składnika środowiska wykonawczego Windows.

2. Zamknij projekt.

3. W **Eksploratora plików Windows**, Znajdź projekt. Domyślnie program Visual Studio używa folder 2017\Projects programu Visual Studio w folderze dokumenty. Znajdź projekt biblioteki języka C++, który zawiera kod, który chcesz przenieść. Skopiuj pliki źródłowe (plików nagłówkowych, pliki kodu i wszelkich innych zasobów, w tym w podkatalogach) z projektu biblioteki języka C++ i wklej je do folderu projektu, upewniając się zachować tę samą strukturę folderów.

4. Otwórz projekt składnika środowiska wykonawczego Windows, a następnie otwórz menu skrótów dla węzła projektu w **Eksploratora rozwiązań**i wybierz polecenie **Dodaj** > **istniejący element**.

5. Zaznacz wszystkie pliki, aby dodać z oryginalnego projektu, a następnie wybierz **OK**. Powtórz w razie potrzeby dla podfolderów.

6. Może teraz niektóre zduplikowano kodu. Jeśli masz więcej niż jeden prekompilowanego nagłówka (np. stdafx.h i pch.h), wybierz jedną do zachowania. Skopiuj cały wymagany kod, takich jak dołączyć instrukcje do tego, który jest zachowywana. Następnie można usunąć właściwości inne, a w projekcie, w obszarze **prekompilowanych nagłówków**, upewnij się, że nazwa pliku nagłówkowego jest poprawna.

   Jeśli zmienisz plik do użycia jako prekompilowanego pliku nagłówkowego, upewnij się, że opcje prekompilowanego nagłówka są poprawne dla każdego pliku. Wybierz kolejno każdy plik .cpp, Otwórz okno właściwości i upewnij się, że wszystkie są ustawione na **użycia (/Yu)**, z wyjątkiem żądaną prekompilowanego pliku nagłówkowego, która powinna być równa **Utwórz (/Yc)**.

7. Skompilować projekt i usuń wszelkie błędy. Te błędy może być spowodowane użyciem `/ZW` opcji lub może być spowodowane przez nową wersję zestawu Windows SDK lub może być odzwierciedlają zależności, np. pliki nagłówkowe, które zależy od biblioteki lub różnice w ustawieniach projektu między starego Projekt i nowy.

8. Dodaj typy publiczne odwołania do projektu lub przekonwertować zwykły typy typach ref, aby udostępnić punkty wejścia do funkcji, którą chcesz wywołać z aplikacji platformy uniwersalnej systemu Windows.

9. Przetestować składnika, dodając do niego odwołanie z projektu aplikacji platformy uniwersalnej systemu Windows, a następnie dodać kod do wywoływania publicznych interfejsów API został utworzony.

## <a name="see-also"></a>Zobacz także

[Przenoszenie na platformę uniwersalną systemu Windows](../porting/porting-to-the-universal-windows-platform-cpp.md)
