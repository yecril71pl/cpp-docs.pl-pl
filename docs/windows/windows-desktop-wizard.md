---
title: Kreator pulpitu systemu Windows
ms.date: 03/29/2019
f1_keywords:
- vc.appwiz.win32.overview
- vc.appwiz.win32.appset
helpviewer_keywords:
- Windows Desktop Wizard
- Win32 Project Wizard
ms.assetid: 5d7b3a5e-8461-479a-969a-67b7883725b9
ms.openlocfilehash: 3d8be0cc33e0435bc5a18191303dbbc91277de0b
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/21/2020
ms.locfileid: "80075450"
---
# <a name="windows-desktop-wizard"></a>Kreator pulpitu systemu Windows

Kreator pulpitu systemu Windows zastępuje Kreatora aplikacji Win32 w programie Visual Studio 2017 i nowszych. Kreator pozwala utworzyć dowolne cztery typy C++ projektów (wymienione w nagłówku w tabeli poniżej). W każdym przypadku można określić dodatkowe opcje, które są odpowiednie dla typu projektu, który zostanie otwarty.

   ![Kreator pulpitu systemu Windows](media/windows-desktop-wizard.png)

Poniższa tabela wskazuje, które opcje są dostępne dla każdego typu aplikacji.

|Typ pomocy technicznej|Aplikacja konsolowa|Aplikacja wykonywalna (Windows)|Biblioteka dołączana dynamicznie|Biblioteka statyczna|
|---------------------|-------------------------|----------------------------------------|---------------------------|--------------------|
|**Pusty projekt**|Yes|Yes|Yes|Nie|
|**Eksportuj symbole**|Nie|Nie|Yes|Nie|
|**Prekompilowany nagłówek**|Nie|Nie|Nie|Yes|
|**Obsługa ATL**|Yes|Nie|Nie|Nie|
|**Obsługa MFC**|Yes|Nie|Nie|Yes|

## <a name="overview"></a>Omówienie

Na tej stronie kreatora opisano bieżące ustawienia projektu dla tworzonej aplikacji Win32. Domyślnie są ustawione następujące opcje:

- Projekt jest aplikacją systemu Windows.

- Projekt nie jest pusty.

- Projekt nie zawiera żadnych symboli eksportu.

- Projekt nie używa prekompilowanego pliku nagłówkowego (Ta opcja jest dostępna tylko w przypadku projektów biblioteki statycznej).

- Projekt zawiera obsługę nie tylko MFC ani ATL.

## <a name="application-type"></a>Typ aplikacji

Tworzy typ określonego typu aplikacji.

|Opcja|Opis|
|------------|-----------------|
|**Aplikacja konsolowa**|Tworzy aplikację konsolową. C++ [Biblioteki uruchomieniowe](../c-runtime-library/c-run-time-library-reference.md) wizualizacji udostępniają również dane wyjściowe i dane wejściowe z okien konsoli za pomocą standardowych funkcji we/wy, takich jak `printf_s()` i `scanf_s()`. Aplikacja konsolowa nie ma graficznego interfejsu użytkownika. Kompiluje się do pliku. exe i może być uruchamiany jako aplikacja autonomiczna z wiersza polecenia.<br /><br /> Do aplikacji konsolowej można dodać obsługę MFC i ATL.|
|**Aplikacja systemu Windows**|Tworzy program Win32. Program Win32 jest aplikacją wykonywalną (EXE) zapisaną w języku C C++lub, przy użyciu wywołań do Win32 API, aby utworzyć graficzny interfejs użytkownika.<br /><br /> Nie można dodać obsługi biblioteki MFC ani ATL do aplikacji systemu Windows.|
|**Biblioteka dołączana dynamicznie**|Tworzy bibliotekę dołączaną dynamicznie (DLL) Win32. Win32 DLL to plik binarny zapisany w języku C lub C++, który używa wywołań do Win32 API, a nie do klas MFC, i działa jako udostępniona biblioteka funkcji, które mogą być używane jednocześnie przez wiele aplikacji.<br /><br /> Nie można dodać obsługi biblioteki MFC ani ATL do aplikacji DLL utworzonej za pomocą tego kreatora, ale można utworzyć bibliotekę MFC DLL, wybierając kolejno pozycje **nowy > Project > MFC DLL**.|
|**Biblioteka statyczna**|Tworzy bibliotekę statyczną. Biblioteka statyczna to plik zawierający obiekty i ich funkcje oraz dane, które łączą się z programem po skompilowaniu pliku wykonywalnego. W tym temacie wyjaśniono, jak utworzyć początkowe pliki i [właściwości projektu](../build/reference/property-pages-visual-cpp.md) dla biblioteki statycznej. Plik biblioteki statycznej zapewnia następujące korzyści:<br /><br />-Biblioteka statyczna Win32 jest przydatna, jeśli aplikacja, nad którą pracujesz, tworzy wywołania do Win32 API, a nie do klas MFC.<br />-Proces łączenia jest taki sam, niezależnie od tego, czy pozostała część aplikacji systemu Windows jest C++zapisywana w C czy w.<br />— Można połączyć bibliotekę statyczną z programem opartym na MFC lub do programu bez MFC.|

## <a name="additional-options"></a>Opcje dodatkowe

Definiuje pomoc techniczną i opcje dla aplikacji, w zależności od jej typu.

|Opcja|Opis|
|------------|-----------------|
|**Pusty projekt**|Określa, że pliki projektu są puste. Jeśli masz zestaw plików kodu źródłowego (takich jak pliki. cpp, pliki nagłówkowe, ikony, paski narzędzi, okna dialogowe itd.) i chcesz utworzyć projekt w środowisku programistycznym Visual C++ , musisz najpierw utworzyć pusty projekt, a następnie dodać pliki do projektu.<br /><br /> Ta opcja jest niedostępna dla projektów biblioteki statycznej.|
|**Eksportuj symbole**|Określa, że projekt DLL eksportuje symbole.|
|**Prekompilowany nagłówek**|Określa, że projekt biblioteki statycznej używa wstępnie skompilowanego nagłówka.|
|**Testy cyklu projektowania zabezpieczeń (SDL)**|Aby uzyskać więcej informacji na temat SDL, zobacz temat [Microsoft Security Development Lifecycle (SDL) wskazówki dotyczące procesu](../build/reference/sdl-enable-additional-security-checks.md)|

## <a name="add-common-headers-for"></a>Dodaj wspólne nagłówki dla:

Dodaj obsługę jednej z bibliotek dostarczonych w wizualizacji C++.

|Opcja|Opis|
|------------|-----------------|
|**ATL**|Kompiluje do obsługi projektu dla klas w Active Template Library (ATL). Tylko dla aplikacji konsolowych Win32.<br /><br /> **Uwaga** Ta opcja nie wskazuje obsługi dodawania obiektów ATL przy użyciu kreatorów kodu ATL. Obiekty ATL można dodawać tylko do projektów ATL lub projektów MFC z obsługą ATL.|
|**BIBLIOTEKI**|Kompiluje do obsługi projektu dla biblioteki Microsoft Foundation Class (MFC). Dotyczy tylko aplikacji konsolowych Win32 i bibliotek statycznych.|

## <a name="remarks"></a>Uwagi

Po utworzeniu aplikacji klasycznej systemu Windows można dodać klasy ogólne C++ przy użyciu kreatora kodu [generycznego](../ide/generic-cpp-class-wizard.md) . Można dodawać inne elementy, takie jak pliki HTML, pliki nagłówkowe, zasoby lub pliki tekstowe.

> [!NOTE]
> Nie można dodać klas ATL i można dodać klasy MFC tylko do tych typów aplikacji klasycznych systemu Windows, które obsługują MFC (patrz Poprzednia tabela).

Możesz wyświetlić pliki tworzone przez kreatora dla projektu w **Eksplorator rozwiązań**. Aby uzyskać więcej informacji na temat plików tworzonych przez kreatora dla projektu, zobacz plik wygenerowany przez projekt, `ReadMe.txt`. Aby uzyskać więcej informacji o typach plików, [typów plików utworzonych dla projektów programu C++ Visual Studio](../build/reference/file-types-created-for-visual-cpp-projects.md).

## <a name="see-also"></a>Zobacz też

[C++typy projektów w programie Visual Studio](../build/reference/visual-cpp-project-types.md)