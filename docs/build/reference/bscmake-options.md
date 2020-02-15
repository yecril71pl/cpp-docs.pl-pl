---
title: Opcje BSCMAKE
description: Informacje o opcjach wiersza polecenia narzędzia Microsoft BSCMAKE.
ms.date: 02/09/2020
f1_keywords:
- VC.Project.VCBscMakeTool.OutputFile
- VC.Project.VCBscMakeTool.SuppressStartupBanner
- VC.Project.VCBscMakeTool.PreserveSBR
helpviewer_keywords:
- /v BSCMAKE option
- Iu BSCMAKE option
- browse information files (.bsc), content
- /Er BSCMAKE option
- NOLOGO BSCMAKE option
- /s BSCMAKE option
- /Ei BSCMAKE option
- /o BSCMAKE option
- /NOLOGO BSCMAKE option
- /Iu BSCMAKE option
- s BSCMAKE option (/s)
- /Em BSCMAKE option
- Em BSCMAKE option
- Es BSCMAKE option
- files [C++], BSCMAKE
- Er BSCMAKE option
- BSCMAKE, options for controlling files
- controlling BSCMAKE options
- El BSCMAKE option
- /El BSCMAKE option
- /Es BSCMAKE option
- Ei BSCMAKE option
ms.assetid: fa2f1e06-c684-41cf-80dd-6a554835ebd2
ms.openlocfilehash: f0fd0e01d3325267ac175435aab65b5d0a9d47ea
ms.sourcegitcommit: 8414cd91297dea88c480e208c7b5301db9972f19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2020
ms.locfileid: "77257796"
---
# <a name="bscmake-options"></a>Opcje BSCMAKE

> [!WARNING]
> Mimo że usługa BSCMAKE jest nadal zainstalowana z programem Visual Studio, nie jest już używana przez IDE. Od programu Visual Studio 2008 informacje dotyczące przeglądania i symboli są przechowywane automatycznie w pliku *`.sdf`* SQL Server w folderze rozwiązania.

Ta sekcja zawiera opis opcji dostępnych do kontrolowania BSCMAKE. Niektóre opcje kontrolują zawartość pliku informacji o przeglądaniu przez wykluczenie lub dołączenie określonych informacji. Opcje wykluczania umożliwiają szybsze działanie BSCMAKE i może spowodować zmniejszenie pliku *`.bsc`* . W nazwach opcji rozróżniana jest wielkość liter (z wyjątkiem **/help** i **/nologo**).

Tylko **/nologo** i **/o** są dostępne w środowisku deweloperskim programu Visual Studio.  Zobacz [Ustawianie C++ właściwości kompilatora i Build w programie Visual Studio](../working-with-project-properties.md) , aby uzyskać informacje na temat dostępu do stron właściwości projektu.

**/EI (** _Nazwa pliku_... **)** \
Wyklucza zawartość określonych plików dołączanych z pliku informacji o przeglądaniu. Aby określić wiele plików, rozdziel nazwy spacjami i umieść je w nawiasach. Nawiasy nie są konieczne, jeśli określono tylko jedną *nazwę pliku*. Użyj **/EI** wraz z opcją **/es** , aby wykluczyć pliki niewykluczone przez **/es**.

**/El**\
Wyklucza symbole lokalne. Wartość domyślna to dołączenie symboli lokalnych. Aby uzyskać więcej informacji na temat symboli lokalnych, zobacz [Tworzenie pliku. sbr](creating-an-dot-sbr-file.md).

**/Em**\
Wyklucza symbole w treści makr. Użyj **/em** , aby uwzględnić tylko nazwy makr w pliku informacji o przeglądaniu. Wartością domyślną jest uwzględnianie zarówno nazw makr, jak i wyników rozwinięcia makra.

**/Er (** _symbol_... **)** \
Wyklucza określone symbole z pliku informacji o przeglądaniu. Aby określić wiele nazw symboli, rozdziel nazwy spacjami i umieść je w nawiasach. Nawiasy są niepotrzebne, jeśli określisz tylko jeden *symbol*.

**/Es**\
Wyklucza każdy plik dyrektywy include określony ze ścieżką bezwzględną lub znajduje się w ścieżce bezwzględnej określonej w zmiennej środowiskowej INCLUDE. (Zwykle te pliki to system plików dołączanych, które zawierają wiele informacji, które mogą nie być potrzebne w pliku informacji o przeglądaniu). Ta opcja nie wyklucza plików określonych bez ścieżki lub ścieżek względnych lub plików znajdujących się w ścieżce względnej w dołączeniu. Do wykluczenia plików, które **/es** nie wykluczają się, można użyć opcji **/EI** wraz z **/es** . Aby wykluczyć tylko niektóre z tych plików, należy użyć **/EI** zamiast **/es**i wyświetlić listę plików, które mają zostać wykluczone.

**/errorReport:** [**Brak** &#124; **monitu o** &#124; &#124; **wysłanie**kolejki] \
Ta opcja jest przestarzała. Począwszy od systemu Windows Vista, raportowanie błędów jest kontrolowane przez ustawienia [raportowanie błędów systemu Windows (wer)](/windows/win32/wer/windows-error-reporting) .

**/Help**\
Wyświetla podsumowanie składni wiersza polecenia BSCMAKE.

**/Iu**\
Zawiera symbole bez odwołań. Domyślnie BSCMAKE nie rejestruje żadnych symboli, które są zdefiniowane, ale nie do odwołania. Jeśli plik *`.sbr`* został spakowany, ta opcja nie ma wpływu na ten plik wejściowy, ponieważ kompilator usunął już symbole, do których nie istnieje odwołanie.

**/n**\
Wymusza nieprzyrostową kompilację. Użyj **/n** , aby wymusić pełną kompilację pliku informacji o przeglądaniu, czy plik *`.bsc`* istnieje, czy nie, i aby zapobiec obcięciu plików *`.sbr`* . Zobacz [, w jaki sposób BSCMAKE kompiluje plik. bsc](how-bscmake-builds-a-dot-bsc-file.md).

**/NOLOGO**\
Pomija komunikat o prawach autorskich BSCMAKE.

**/o** *filename*\
Określa nazwę pliku informacji o przeglądaniu. Domyślnie BSCMAKE udostępnia plik informacji o przeglądaniu nazwą podstawową pierwszego pliku *`.sbr`* i rozszerzenia *`.bsc`* .

**/S (** _filename_... **)** \
Informuje BSCMAKE, aby przetworzyć określony plik dołączany przy pierwszym napotkaniu i wykluczeniu go w inny sposób. Użyj tej opcji, aby zaoszczędzić czas przetwarzania, gdy plik (taki jak nagłówek lub *`.h`* , plik dla *`.c`* lub *`.cpp`* plik źródłowy) jest uwzględniony w kilku plikach źródłowych, ale jest niezmieniony przez poszczególne dyrektywy przetwarzania wstępnego. Użyj tej opcji, jeśli plik zostanie zmieniony w sposób nieistotny dla tworzonego pliku informacji o przeglądaniu. Aby określić wiele plików, rozdziel nazwy spacjami i umieść je w nawiasach. Nawiasy nie są konieczne, jeśli określono tylko jedną *nazwę pliku*. Jeśli chcesz wykluczyć plik za każdym razem, gdy zostanie on uwzględniony, użyj opcji **/EI** lub **/es** .

**/v**\
Zawiera pełne dane wyjściowe, w tym nazwy poszczególnych plików *`.sbr`* przetwarzanych i informacje o kompletnym przebiegu BSCMAKE.

**/?** \
Wyświetla krótkie podsumowanie składni wiersza polecenia BSCMAKE.

Poniższy wiersz polecenia informuje BSCMAKE o konieczności wykonania pełnej kompilacji pliku MAIN. bsc z trzech *`.sbr`* plików. Informuje również BSCMAKE o wykluczeniu zduplikowanych wystąpień PRZYBORNIKa. h:

```cmd
BSCMAKE /n /S toolbox.h /o main.bsc file1.sbr file2.sbr file3.sbr
```

## <a name="see-also"></a>Zobacz też

[BSCMAKE — dokumentacja](bscmake-reference.md)
