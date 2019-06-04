---
title: Kreator aplikacji klasycznej Windows
ms.date: 03/29/2019
f1_keywords:
- vc.appwiz.win32.overview
- vc.appwiz.win32.appset
helpviewer_keywords:
- Windows Desktop Wizard
- Win32 Project Wizard
ms.assetid: 5d7b3a5e-8461-479a-969a-67b7883725b9
ms.openlocfilehash: 2f9ac262cc564c39d30ddfae7f70ea92e92081a8
ms.sourcegitcommit: ecf274bcfe3a977c48745aaa243e5e731f1fdc5f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2019
ms.locfileid: "66503797"
---
# <a name="windows-desktop-wizard"></a>Kreator aplikacji klasycznej Windows

Kreator pulpitu Windows zastępuje Kreatora aplikacji Win32, w programie Visual Studio 2017 i nowszych wersjach. Kreator umożliwia tworzenie każdego z czterech typów projektów w języku C++ (wyszczególnionych w nagłówku w poniższej tabeli). W każdym przypadku można określić dodatkowe opcje, które są odpowiednie dla typu projektu, które można otworzyć. 

   ![Kreator aplikacji klasycznej Windows](media/windows-desktop-wizard.png)

Poniższa tabela wskazuje, które opcje są dostępne dla każdego typu aplikacji.

|Typ obsługi|Aplikacja konsolowa|Aplikacja pliku wykonywalnego (Windows)|Biblioteka dołączana dynamicznie|Biblioteka statyczna|
|---------------------|-------------------------|----------------------------------------|---------------------------|--------------------|
|**Pusty projekt**|Yes|Yes|Yes|Nie|
|**Eksportuj symbole**|Nie|Nie|Yes|Nie|
|**Prekompilowany plik nagłówkowy**|Nie|Nie|Nie|Tak|
|**Obsługa biblioteki ATL**|Tak|Nie|Nie|Nie|
|**Obsługa MFC**|Tak|Nie|Nie|Tak|

## <a name="overview"></a>Omówienie

Ta strona kreatora opisuje bieżące ustawienia projektu dla aplikacji Win32, którą tworzysz. Domyślnie ustawiony są następujące opcje:

- Projekt jest w aplikacji Windows.

- Projekt nie jest pusty.

- Projekt nie zawiera symboli eksportu.

- Projekt nie korzysta z prekompilowanego pliku nagłówka (Ta opcja jest dostępna dla projektów biblioteki statycznej tylko).

- Projekt obejmuje obsługę MFC ani ATL.

## <a name="application-type"></a>Typ aplikacji

Tworzy typ określonej aplikacji.

|Opcja|Opis|
|------------|-----------------|
|**Aplikacja konsolowa**|Tworzy aplikację konsoli. Visual C++ [biblioteki wykonawczej](../c-runtime-library/c-run-time-library-reference.md) również podać dane wyjściowe i dane wejściowe z okna konsoli za pomocą funkcji standardowych operacji We/Wy, takich jak `printf_s()` i `scanf_s()`. Aplikacja konsolowa nie ma graficznego interfejsu użytkownika. On kompilowany na plik .exe i mogą być uruchamiane jako autonomiczną aplikację z poziomu wiersza polecenia.<br /><br /> Możesz dodać obsługę MFC i ATL do aplikacji konsoli.|
|**Aplikacja Windows**|Powoduje utworzenie programu systemu Win32. Programu systemu Win32 jest aplikacja pliku wykonywalnego (EXE) w języku C lub C++, tworzenie graficznego interfejsu użytkownika przy użyciu wywołania funkcji API Win32.<br /><br /> Nie można dodać MFC lub ATL Obsługa aplikacji Windows.|
|**Biblioteka dołączana dynamicznie**|Tworzy Win32 biblioteki dołączanej (dynamicznie DLL). Biblioteka DLL systemu Win32 jest plik binarny, napisany w języku C lub C++, który używa wywołania funkcji API Win32, a nie do klas MFC i który działa jako współdzielona biblioteka funkcji, które mogą być używane jednocześnie przez wiele aplikacji.<br /><br /> Nie można dodać obsługę biblioteki ATL i MFC do biblioteki DLL aplikacji utworzony za pomocą tego kreatora, ale można utworzyć biblioteki MFC DLL, należy wybrać **nowy > Projekt > biblioteki MFC DLL**.|
|**Biblioteka statyczna**|Tworzy bibliotekę statyczną. Biblioteka statyczna jest plikiem zawierającym obiektów i ich funkcje i dane, który stanowi łącze do tego programu, podczas kompilowania pliku wykonywalnego. W tym temacie opisano sposób tworzenia plikach startowych i [właściwości projektu](../build/reference/property-pages-visual-cpp.md) dla biblioteki statycznej. Plik biblioteki statycznej zapewnia następujące korzyści:<br /><br />Biblioteka statyczna Win32 jest przydatne w przypadku aplikacji, którą pracujesz nad wywołań interfejsu API Win32, a nie do klas MFC.<br />— Proces łączenia jest taki sam, czy w pozostałej części aplikacji Windows są zapisywane w języku C lub C++.<br />— Biblioteka statyczna możesz połączyć program oparty na bibliotece MFC lub program innego typu niż MFC.|

## <a name="additional-options"></a>Dodatkowe opcje

Definiuje pomocy technicznej i opcje dla aplikacji, w zależności od jego typu.

|Opcja|Opis|
|------------|-----------------|
|**Pusty projekt**|Określa, że pliki projektu są puste. Jeśli masz zestaw plików kodu źródłowego (na przykład plików .cpp, pliki nagłówkowe, ikony, paski narzędzi, okna dialogowe i tak dalej) i chcesz utworzyć projekt w środowisku programowania Visual C++, użytkownik musi najpierw utwórz pusty projekt, a następnie dodaj pliki do projektu.<br /><br /> Zaznacz to pole wyboru jest niedostępny dla projektów biblioteki statycznej.|
|**Eksportuj symbole**|Określa, że projekt DLL eksportuje symboli.|
|**Prekompilowany plik nagłówkowy**|Określa, że projekt biblioteki statycznej używa wstępnie skompilowanym nagłówkiem.|
|**Sprawdza, czy cykl projektowania zabezpieczeń (SDL)**|Aby uzyskać więcej informacji na temat SDL, zobacz [wskazówek dotyczących procesu cykl projektowania zabezpieczeń (SDL)](../build/reference/sdl-enable-additional-security-checks.md)|

## <a name="add-common-headers-for"></a>Dodaj wspólne nagłówki dla:

Dodano obsługę jednej z bibliotek dostarczane w programie Visual C++.

|Opcja|Opis|
|------------|-----------------|
|**ATL**|Kompilacje do obsługi projektu dla klas w Active Template Library (ATL). Win32 console tylko dla aplikacji.<br /><br /> **Uwaga** tej opcji nie oznacza Obsługa dodawania obiektów ATL za pomocą ATL kodu kreatorów. Obiekty ATL można dodawać tylko do projektów ATL lub projektów MFC z biblioteki ATL pomocy technicznej.|
|**MFC**|Kompilacje do obsługi projektu biblioteki Microsoft Foundation Class (MFC). Aplikacje konsoli Win32 i tylko w przypadku bibliotek statycznych.|

## <a name="remarks"></a>Uwagi

Po utworzeniu aplikacji pulpitu Windows można dodać ogólne klasy C++ za pomocą [ogólny](../ide/generic-cpp-class-wizard.md) kreatora kodów. Możesz dodać inne elementy, takie jak pliki HTML, pliki nagłówka, zasoby lub pliki tekstowe.

> [!NOTE]
> Nie można dodawać klas ALT, a klasy MFC można dodawać tylko do tych typów aplikacji klasycznych Windows, które obsługują MFC (zob. Poprzednia tabela).

Można wyświetlić pliki, Kreator tworzy projekt w **Eksploratora rozwiązań**. Aby uzyskać więcej informacji o plikach, Kreator tworzy dla projektu, zobacz plik wygenerowany przez projekt `ReadMe.txt`. Aby uzyskać więcej informacji dotyczących typów plików [typy plików utworzonych dla programu Visual Studio C++ projektów](../build/reference/file-types-created-for-visual-cpp-projects.md).

## <a name="see-also"></a>Zobacz także

[C++typy projektów w programie Visual Studio](../build/reference/visual-cpp-project-types.md)