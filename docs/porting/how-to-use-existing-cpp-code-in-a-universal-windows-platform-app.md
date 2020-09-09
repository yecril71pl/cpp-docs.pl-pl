---
title: 'Instrukcje: Używanie istniejącego kodu C++ w aplikacji platformy uniwersalnej systemu Windows'
description: Sposoby używania istniejących aplikacji i bibliotek kodu w aplikacjach platforma uniwersalna systemu Windows.
ms.date: 09/04/2020
ms.assetid: 87e5818c-3081-42f3-a30d-3dca2cf0645c
ms.openlocfilehash: 1e946d588f1a14018ebb11a60b319c2d54658f25
ms.sourcegitcommit: 0df2b7ab4e81284c5248e4584767591dcc1950c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/09/2020
ms.locfileid: "89609131"
---
# <a name="how-to-use-existing-c-code-in-a-universal-windows-platform-app"></a>Instrukcje: Używanie istniejącego kodu C++ w aplikacji platformy uniwersalnej systemu Windows

Istnieją różne sposoby używania istniejącego kodu C++ w projektach platforma uniwersalna systemu Windows (platformy UWP). Niektóre z nich nie wymagają ponownej kompilacji kodu z włączonymi rozszerzeniami składników (C++/CX) (czyli z `/ZW` opcją), a kilka. Być może trzeba będzie zachować kod w standardowym języku C++ lub zachować klasyczne środowisko kompilacji Win32 dla pewnego kodu. Nadal możesz to zrobić, korzystając z odpowiednich opcji architektury. Rozważmy cały kod, który zawiera interfejs użytkownika platformy UWP i typy, które są dostępne dla wywołujących C#, Visual Basic i JavaScript. Ten kod powinien znajdować się w projektach aplikacji systemu Windows i projektach składników środowisko wykonawcze systemu Windows. Kod, który jest wywoływany tylko z języka C++ (w tym C++/CX), może być w projekcie, który kompiluje się przy użyciu `/ZW` opcji lub standardowego projektu języka C++. Kod tylko binarny, który nie używa niedozwolonych interfejsów API, może być używany przez połączenie go jako biblioteki statycznej. Można też spakować ją z aplikacją jako zawartość i załadować ją w bibliotece DLL.

Prawdopodobnie najprostszym sposobem na rozpoczęcie pracy programu klasycznego w środowisku platformy UWP jest użycie technologii mostka dla komputerów stacjonarnych. Obejmują one konwerter aplikacji klasycznych, który spowoduje spakowanie istniejącej aplikacji jako aplikacji platformy UWP bez konieczności wprowadzania zmian w kodzie. Aby uzyskać więcej informacji, zobacz [mostek Desktop](/windows/uwp/porting/desktop-to-uwp-root).

W dalszej części tego artykułu omówiono sposób przenoszenia bibliotek C++ (bibliotek DLL i bibliotek statycznych) do platforma uniwersalna systemu Windows. Możesz chcieć przenieść kod, aby można było używać logiki core C++ z wieloma aplikacjami platformy UWP.

Aplikacje platformy UWP działają w środowisku chronionym. W związku z tym wiele wywołań interfejsu API systemu Win32, COM i CRT, które mogą naruszać bezpieczeństwo platformy, nie są dozwolone. `/ZW`Opcja kompilatora może wykryć takie wywołania i wygenerować błąd. Możesz użyć zestawu certyfikacji aplikacji w swojej aplikacji, aby wykryć kod, który wywołuje niedozwolone interfejsy API. Aby uzyskać więcej informacji, zobacz [zestaw certyfikacji aplikacji systemu Windows](/windows/uwp/debug-test-perf/windows-app-certification-kit).

Jeśli dla biblioteki jest dostępny kod źródłowy, można spróbować wyeliminować niedozwolone wywołania interfejsu API. Aby zapoznać się z listą interfejsów API, które nie są dozwolone, zobacz [interfejsy API Win32 i com dla aplikacji platformy UWP](/uwp/win32-and-com/win32-and-com-for-uwp-apps) i [funkcje CRT nieobsługiwane w aplikacjach platforma uniwersalna systemu Windows](../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md). Niektóre alternatywy można znaleźć w temacie [alternatywy dla interfejsów API systemu Windows w aplikacjach platformy UWP](/uwp/win32-and-com/alternatives-to-windows-apis-uwp).

Jeśli po prostu próbujesz dodać odwołanie z uniwersalnego projektu systemu Windows do klasycznej biblioteki pulpitów, zostanie wyświetlony komunikat o błędzie informujący, że biblioteka nie jest zgodna. Jeśli jest to Biblioteka statyczna, możesz połączyć się z biblioteką, dodając bibliotekę ( *`.lib`* plik) do danych wejściowych konsolidatora, tak samo jak w klasycznej aplikacji Win32. Jeśli dostępna jest tylko biblioteka binarna, jest to jedyna opcja. Biblioteka statyczna jest połączona z plikiem wykonywalnym aplikacji. Jednak biblioteka Win32 DLL, która jest zużywana w aplikacji platformy UWP, musi być pakowana do aplikacji przez dołączenie jej do projektu i oznaczenie jej jako zawartości. Aby załadować bibliotekę DLL Win32 w aplikacji platformy UWP, należy również wywołać [`LoadPackagedLibrary`](/windows/win32/api/winbase/nf-winbase-loadpackagedlibrary) zamiast `LoadLibrary` lub `LoadLibraryEx` .

Jeśli masz kod źródłowy biblioteki DLL lub statycznej, możesz ponownie skompilować go jako projekt platformy UWP przy użyciu `/ZW` opcji kompilatora. Następnie można dodać odwołanie do niego przy użyciu **Eksplorator rozwiązań**i używać go w aplikacjach C++ platformy UWP. Połącz bibliotekę DLL przy użyciu biblioteki eksportu.

Aby uwidocznić funkcjonalność dla obiektów wywołujących w innych językach, można skonwertować bibliotekę na składnik środowisko wykonawcze systemu Windows. Składniki środowisko wykonawcze systemu Windows różnią się od zwykłych bibliotek DLL w tym, że zawierają metadane w postaci *`.winmd`* plików, które opisują zawartość w sposób, w jaki użytkownicy platformy .NET i języka JavaScript potrzebują.  Aby uwidocznić elementy interfejsu API w innych językach, można dodać konstrukcje C++/CX, takie jak klasy ref, i udostępnić je publicznie. W systemie Windows 10 i nowszych zaleca się użycie [biblioteki c++/WinRT](https://github.com/microsoft/cppwinrt) zamiast języka c++/CX.

Powyższe dyskusje nie dotyczą składników modelu COM, które muszą być obsługiwane inaczej. Jeśli w pliku EXE lub DLL znajduje się serwer COM, można go użyć w uniwersalnym projekcie systemu Windows. Spakuj go jako [składnik COM bez rejestracji](/windows/win32/sbscs/creating-registration-free-com-objects), Dodaj go do projektu jako plik zawartości i utwórz jego wystąpienie przy użyciu [`CoCreateInstanceFromApp`](/windows/win32/api/combaseapi/nf-combaseapi-cocreateinstancefromapp) . Aby uzyskać więcej informacji, zobacz [Korzystanie z biblioteki DLL Free-com w projekcie w Sklepie Windows w języku C++](/archive/blogs/win8devsupport/using-free-com-dll-in-windows-store-c-project).

Jeśli chcesz przenieść istniejącą bibliotekę COM do platformy UWP, możliwe jest również przekonwertowanie jej na składnik środowisko wykonawcze systemu Windows. Zalecamy użycie biblioteki C++/WinRT dla takich portów, ale możliwe jest również korzystanie z [środowisko wykonawcze systemu Windows biblioteki szablonów c++ (WRL)](../windows/windows-runtime-cpp-template-library-wrl.md). WRL jest przestarzała i nie obsługuje wszystkich funkcji ATL i OLE. Czy taki port jest wykonalny, zależy od funkcji COM, ATL i OLE, których wymaga składnik.

W zależności od wybranych scenariuszy programistycznych należy pamiętać o kilku definicjach makr. Możesz użyć tych makr w kodzie, aby kompilować kod warunkowo w klasycznym środowisku Win32 i platformy UWP.

```cpp
#if WINAPI_FAMILY_PARTITION(WINAPI_PARTITION_PC_APP)
#if WINAPI_FAMILY_PARTITION(WINAPI_PARTITION_PHONE_APP)
#if WINAPI_FAMILY_PARTITION(WINAPI_PARTITION_APP)
#if WINAPI_FAMILY_PARTITION(WINAPI_PARTITION_DESKTOP)
```

Te instrukcje dotyczą odpowiednio aplikacji platformy UWP, aplikacji ze sklepu Windows Phone, obu lub nie (tylko klasyczny pulpit Win32). Te makra są dostępne tylko w Windows SDK 8,1 i nowszych.

Ten artykuł zawiera następujące procedury:

- [Korzystanie z biblioteki Win32 DLL w aplikacji platformy UWP](#BK_Win32DLL)

- [Używanie natywnej biblioteki statycznej języka C++ w aplikacji platformy UWP](#BK_StaticLib)

- [Przenoszenie biblioteki C++ do składnika środowisko wykonawcze systemu Windows](#BK_WinRTComponent)

## <a name="using-a-win32-dll-in-a-uwp-app"></a><a name="BK_Win32DLL"></a> Korzystanie z biblioteki Win32 DLL w aplikacji platformy UWP

Aby zapewnić lepsze zabezpieczenia i niezawodność, aplikacje uniwersalne systemu Windows działają w ograniczonym środowisku wykonawczym. Nie można po prostu użyć żadnej natywnej biblioteki DLL w sposób klasyczny aplikacji klasycznej systemu Windows. Jeśli masz kod źródłowy dla biblioteki DLL, możesz przenieść kod tak, aby był on uruchamiany w platformy UWP. Zacznij od zmiany kilku ustawień projektu i metadanych pliku projektu, aby zidentyfikować projekt jako projekt platformy UWP. Należy ponownie skompilować kod biblioteki przy użyciu `/ZW` opcji, która umożliwia C++/CX. Niektóre wywołania interfejsu API są niedozwolone w aplikacjach platformy UWP z powodu ściślejszych kontroli skojarzonych z tym środowiskiem. Aby uzyskać więcej informacji, zobacz [Win32 and com API for platformy UWP Apps](/uwp/win32-and-com/win32-and-com-for-uwp-apps).

Jeśli masz natywną bibliotekę DLL, która eksportuje funkcje przy użyciu `__declspec(dllexport)` , możesz wywołać te funkcje z poziomu aplikacji platformy UWP przez ponowną kompilację biblioteki DLL jako projektu platformy UWP. Załóżmy na przykład, że mamy projekt Win32 DLL o nazwie *Giraffe* , który eksportuje kilka klas i ich metod, przy użyciu kodu, takiego jak następujący plik nagłówkowy:

```cpp
// giraffe.h
// Define GIRAFFE_EXPORTS when building this DLL
#pragma once

#ifdef GIRAFFE_EXPORTS
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
#include "pch.h"
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

Wszystkie inne elementy w projekcie ( *`pch.h`* , *`dllmain.cpp`* ) są częścią standardowego szablonu projektu środowiska Win32. Kod definiuje makro `GIRAFFE_API` , które jest rozpoznawane jako, `__declspec(dllexport)` gdy `GIRAFFE_EXPORTS` jest zdefiniowane. Oznacza to, że jest on definiowany, gdy projekt jest skompilowany jako biblioteka DLL, ale nie w przypadku, gdy klient używa *`giraffe.h`* nagłówka. Ta biblioteka DLL może być używana w projekcie platformy UWP bez zmiany kodu źródłowego. Należy zmienić tylko niektóre ustawienia projektu i właściwości.

Poniższa procedura ma zastosowanie w przypadku natywnej biblioteki DLL, która uwidacznia funkcje przy użyciu `__declspec(dllexport)` .

### <a name="to-port-a-native-dll-to-the-uwp-without-creating-a-new-project"></a>Aby przenieść natywną bibliotekę DLL do platformy UWP bez tworzenia nowego projektu

1. Otwórz projekt DLL w programie Visual Studio.

1. Otwórz **właściwości projektu** dla projektu DLL i ustaw **konfigurację** na **wszystkie konfiguracje**.

1. We **właściwościach projektu**, na karcie Ogólne **C/C++**  >  **General** ustaw wartość Użyj **środowisko wykonawcze systemu Windows Extension** na **tak (/zw)**. Ta właściwość włącza rozszerzenia składników (C++/CX).

1. W **Eksplorator rozwiązań**wybierz węzeł projektu, otwórz menu skrótów, a następnie wybierz polecenie **Zwolnij projekt**. Następnie otwórz menu skrótów w węźle niezaładowanego projektu, a następnie wybierz polecenie Edytuj plik projektu. Znajdź `WindowsTargetPlatformVersion` element i zastąp go następującymi elementami.

    ```xml
    <AppContainerApplication>true</AppContainerApplication>
    <ApplicationType>Windows Store</ApplicationType>
    <WindowsTargetPlatformVersion>10.0.10156.0</WindowsTargetPlatformVersion>
    <WindowsTargetPlatformMinVersion>10.0.10156.0</WindowsTargetPlatformMinVersion>
    <ApplicationTypeRevision>10.0</ApplicationTypeRevision>
    ```

   Zamknij *`.vcxproj`* plik, ponownie otwórz menu skrótów, a następnie wybierz polecenie **Załaduj ponownie projekt**.

   **Eksplorator rozwiązań** teraz identyfikuje projekt jako uniwersalny projekt systemu Windows.

1. Upewnij się, że nazwa pliku prekompilowanego nagłówka jest poprawna. W sekcji **prekompilowane nagłówki** może zajść potrzeba zmiany **prekompilowanego pliku nagłówkowego** z *`pch.h`* na *`stdafx.h`* lub w inny sposób, Jeśli zobaczysz błąd podobny do tego:

   > błąd C2857: Instrukcja "#include" określona z **`/Ycpch.h`** opcją wiersza polecenia nie została znaleziona w pliku źródłowym

   Problem polega na tym, że starsze szablony projektu używają innej konwencji nazewnictwa dla prekompilowanego pliku nagłówkowego. Projekty programu Visual Studio 2019 i nowszych używają *`pch.h`* .

1. Skompiluj projekt. Mogą wystąpić błędy dotyczące niezgodnych opcji wiersza polecenia. Na przykład obecnie przestarzałe, ale często używane opcje Włącz minimalną ponowną kompilację **(/GM)** jest domyślnie ustawiona w wielu starszych projektach C++ i jest niezgodna z `/ZW` .

   Niektóre funkcje nie są dostępne podczas kompilowania dla platforma uniwersalna systemu Windows. Zobaczysz błędy kompilatora dotyczące wszelkich problemów. Usuń te błędy do momentu, aż będziesz mieć czystą kompilację.

1. Aby użyć biblioteki DLL w aplikacji platformy UWP w tym samym rozwiązaniu, otwórz menu skrótów dla węzła projektu platformy UWP i wybierz polecenie **Dodaj**  >  **odwołanie**.

   W obszarze **projekty**  >  **rozwiązania**zaznacz pole wyboru obok projektu DLL, a następnie wybierz przycisk **OK** .

1. Uwzględnij pliki nagłówkowe biblioteki w pliku aplikacji platformy UWP *`pch.h`* .

    ```cpp
    #include "..\Giraffe\giraffe.h"
    ```

1. Dodaj kod w zwykły sposób w projekcie platformy UWP, aby wywoływać funkcje i tworzyć typy z biblioteki DLL.

    ```cpp
    MainPage::MainPage()
    {
        InitializeComponent();
        GiraffeFactory gf;
        Giraffe* g = gf.Create();
        int id = g->GetID();
    }
    ```

## <a name="using-a-native-c-static-library-in-a-uwp-app"></a><a name="BK_StaticLib"></a> Używanie natywnej biblioteki statycznej języka C++ w aplikacji platformy UWP

W projekcie platformy UWP można użyć natywnej biblioteki statycznej C++, ale istnieją pewne ograniczenia i ograniczenia, które należy znać. Zacznij od odczytywania [bibliotek statycznych w języku C++/CX](../cppcx/static-libraries-c-cx.md). Możesz uzyskać dostęp do kodu natywnego w bibliotece statycznej z aplikacji platformy UWP, ale nie zaleca się tworzenia publicznych typów referencyjnych w takiej bibliotece statycznej. W przypadku kompilowania biblioteki statycznej z `/ZW` opcją bibliotekarza (w rzeczywistości konsolidator w przebraniu) ostrzega:

> LNK4264: archiwizowanie pliku obiektu skompilowanego z/ZW w bibliotece statycznej; należy pamiętać, że podczas tworzenia typów środowisko wykonawcze systemu Windows nie zaleca się łączenia z biblioteką statyczną zawierającą środowisko wykonawcze systemu Windows metadanych

Można jednak użyć biblioteki statycznej w aplikacji platformy UWP bez ponownego kompilowania jej przy użyciu programu `/ZW` . Biblioteka nie może zadeklarować żadnych typów referencyjnych ani używać konstrukcji C++/CX. Ale jeśli celem jest tylko użycie biblioteki kodu natywnego, można to zrobić, wykonując następujące kroki.

### <a name="to-use-a-native-c-static-library-in-a-uwp-project"></a>Aby użyć natywnej biblioteki statycznej C++ w projekcie platformy UWP

1. We właściwościach projektu dla projektu platformy UWP wybierz pozycję **Właściwości konfiguracji**  >  **Linker**  >  **dane wejściowe** konsolidatora w okienku po lewej stronie. W okienku po prawej stronie Dodaj ścieżkę do biblioteki we właściwości **dodatkowe zależności** . Na przykład dla biblioteki w projekcie, która umieszcza dane wyjściowe w *`<SolutionFolder>\Debug\MyNativeLibrary\MyNativeLibrary.lib`* , Dodaj ścieżkę względną *`Debug\MyNativeLibrary\MyNativeLibrary.lib`* .

1. Dodaj instrukcję include, aby odwołać się do pliku nagłówkowego do *`pch.h`* pliku (jeśli istnieje) lub w dowolnym *`.cpp`* pliku w razie potrzeby, a następnie zacznij dodawać kod, który używa biblioteki.

   ```cpp
   #include "..\MyNativeLibrary\MyNativeLibrary.h"
   ```

   Nie dodawaj odwołania w węźle **odwołania** w **Eksplorator rozwiązań**. Ten mechanizm działa tylko w przypadku składników środowisko wykonawcze systemu Windows.

## <a name="porting-a-c-library-to-a-windows-runtime-component"></a><a name="BK_WinRTComponent"></a> Przenoszenie biblioteki C++ do składnika środowisko wykonawcze systemu Windows

Załóżmy, że chcesz korzystać z natywnych interfejsów API w bibliotece statycznej z poziomu aplikacji platformy UWP. Jeśli masz kod źródłowy biblioteki natywnej, możesz przenieść kod do składnika środowisko wykonawcze systemu Windows. Nie jest już biblioteką statyczną; spowoduje to przekształcenie do biblioteki DLL, której można użyć w dowolnej aplikacji C++ platformy UWP. W tej procedurze opisano sposób tworzenia nowego składnika środowisko wykonawcze systemu Windows, który używa rozszerzeń C++/CX. Aby uzyskać informacje na temat tworzenia składnika korzystającego z języka C++/WinRT, zobacz [środowisko wykonawcze systemu Windows Components with c++/WinRT](/windows/uwp/winrt-components/create-a-windows-runtime-component-in-cppwinrt).

W przypadku korzystania z języka C++/CX można dodawać typy referencyjne i inne konstrukcje języka C++/CX, które są dostępne dla klientów w dowolnym kodzie aplikacji platformy UWP. Możesz uzyskać dostęp do tych typów z poziomu języka C#, Visual Basic lub JavaScript. Podstawowa procedura:

- Utwórz projekt składnika środowisko wykonawcze systemu Windows (system uniwersalny Windows),
- Skopiuj kod biblioteki statycznej do niej, a następnie
- należy rozwiązać wszelkie błędy kompilatora spowodowane przez `/ZW` opcję.

### <a name="to-port-a-c-library-to-a-windows-runtime-component"></a>Aby przenieść bibliotekę języka C++ do składnika środowisko wykonawcze systemu Windows

1. Utwórz projekt składnika środowisko wykonawcze systemu Windows (uniwersalny system Windows).

1. Zamknij projekt.

1. Zlokalizuj nowy projekt w **Eksploratorze plików systemu Windows**. Następnie zlokalizuj projekt biblioteki C++ zawierający kod, który chcesz przenieść. Skopiuj pliki źródłowe (pliki nagłówkowe, pliki kodu i inne zasoby, w tym w podkatalogach) z projektu biblioteki języka C++. Wklej je do folderu nowy projekt, aby zachować tę samą strukturę folderów.

1. Otwórz ponownie projekt składnika środowisko wykonawcze systemu Windows. Otwórz menu skrótów dla węzła projektu w **Eksplorator rozwiązań**i wybierz polecenie **Dodaj**  >  **istniejący element**.

1. Zaznacz wszystkie pliki, które mają zostać dodane z oryginalnego projektu, a następnie wybierz **przycisk OK**. Powtórz w razie potrzeby dla podfolderów.

1. Może teraz istnieć pewien duplikat kodu. Jeśli istnieje więcej niż jeden prekompilowany nagłówek (Powiedz, oba *`stdafx.h`* i *`pch.h`* ), wybierz jeden do zachowania. Skopiuj dowolny wymagany kod, taki jak instrukcje include, do tej, która jest zachowywana. Następnie usuń inne, a we właściwościach projektu w obszarze **prekompilowane nagłówki**upewnij się, że nazwa pliku nagłówka jest poprawna.

   Jeśli plik został zmieniony tak, aby używał jako prekompilowanego nagłówka, upewnij się, że opcje prekompilowanego nagłówka są poprawne dla każdego pliku. Zaznacz każdy *`.cpp`* plik z kolei, otwórz jego okno właściwości i upewnij się, że wszystkie są ustawione na wartość **Użyj (/Yu)**, z wyjątkiem prekompilowanego nagłówka, który powinien być ustawiony na **Utwórz (/Yc)**.

1. Skompiluj projekt i Usuń wszelkie błędy. Te błędy mogą być spowodowane użyciem `/ZW` opcji lub mogą być spowodowane przez nową wersję Windows SDK. Lub mogą one odzwierciedlać zależności, takie jak pliki nagłówkowe, od których zależy Twoja biblioteka, lub różnice w ustawieniach projektu między starym projektem a nowym.

1. Dodaj publiczne typy odwołań do projektu lub przekonwertuj typy zwykłe na typy referencyjne. Te typy umożliwiają udostępnianie punktów wejścia do funkcji, które mają być wywoływane z aplikacji platformy UWP.

1. Przetestuj składnik, dodając odwołanie do niego z projektu aplikacji platformy UWP i dodając kod do wywoływania publicznych interfejsów API, które zostały utworzone.

## <a name="see-also"></a>Zobacz też

[Przenoszenie do platforma uniwersalna systemu Windows](../porting/porting-to-the-universal-windows-platform-cpp.md)
