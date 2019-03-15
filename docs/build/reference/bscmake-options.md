---
title: Opcje BSCMAKE
ms.date: 11/04/2016
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
ms.openlocfilehash: bf4c3648079dff16481dbdd56b9a70093fd22d8d
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57812060"
---
# <a name="bscmake-options"></a>Opcje BSCMAKE

W tej sekcji opisano opcjami dostępnymi na potrzeby kontrolowania BSCMAKE. Kilka opcji kontrolować zawartość pliku informacyjnego przeglądarki, z wyłączeniem lub pewne informacje w tym. Opcje wykluczenia umożliwia BSCMAKE odbywało się szybciej i może skutkować mniejszą pliku .bsc. Opcja nazwy jest uwzględniana wielkość liter (z wyjątkiem **/HELP** i **/nologo**).

Tylko **/nologo** i **/o** są dostępne z poziomu środowiska programistycznego Visual Studio.  Zobacz [kompilatora i tworzenia właściwości ustaw C++ w programie Visual Studio](../working-with-project-properties.md) uzyskać informacji na temat dostępu do strony właściwości projektu.

**/EI (** *filename*... **)**<br/>
Pomija zawartość plików określonegop dołączanego pliku informacyjnego przeglądarki. Do określenia wielu plików, nazwy należy oddzielić spacjami i ująć listę w nawiasach. Nawiasy nie są konieczne, jeśli określisz tylko jeden *filename*. Użyj **/Ei** wraz z **/Es** opcję, aby wykluczyć pliki nie zostały wyłączone przez **/Es**.

**/El**<br/>
Wyklucza symboli lokalnych. Wartość domyślna to dołączać symbole lokalne. Aby uzyskać więcej informacji na temat symboli lokalnych, zobacz [Tworzenie pliku .sbr](creating-an-dot-sbr-file.md).

**/Em**<br/>
Wyklucza symbole w ciele makra. Użyj **/Em** obejmujący tylko nazwy makra w pliku informacyjnego przeglądarki. Wartość domyślna to do nazw makr i wynik makra rozszerzenia.

**/ER (** *symbol*... **)**<br/>
Pomija symbole określonego pliku informacyjnego przeglądarki. Aby określić wiele nazw symboli, nazwy należy oddzielić spacjami i ująć listę w nawiasach. Nawiasy nie są konieczne, jeśli określisz tylko jeden *symbol*.

**/Es**<br/>
Wyklucza z pliku informacyjnego przeglądarki każdego pliku dołączanego określony za pomocą ścieżką bezwzględną, lub znaleźć ścieżka bezwzględna określone w zmiennej środowiskowej INCLUDE. (Zazwyczaj są to system plików dołączanych, które zawierają wiele informacji, które mogą nie być potrzebne w pliku informacji przeglądania.) Ta opcja nie wyklucza określono bez ścieżki lub ścieżek względnych plików znalezionych w ścieżki względnej w DOŁĄCZANIA plików. Możesz użyć **/Ei** wraz z opcją **/Es** Aby wykluczyć pliki **/Es** nie wyklucza. Jeśli chcesz wykluczyć niektóre pliki, **/Es** wyklucza, użyj **/Ei** zamiast **/Es** i wyświetlić listę plików, które chcesz wykluczyć.

**/errorreport:**[**none** &#124; **prompt** &#124; **queue** &#124; **send**]<br/>
Umożliwia wysyłanie informacji do firmy Microsoft dotyczące błędów wewnętrznych w bscmake.exe.

Aby uzyskać więcej informacji na temat **/errorreport**, zobacz [/errorreport (zgłaszaj wewnętrzne błędy kompilatora)](errorreport-report-internal-compiler-errors.md).

**/HELP**<br/>
Przedstawia podsumowanie składni wiersza polecenia BSCMAKE.

**/IU**<br/>
Zawiera symbole bez odwołań. Domyślnie BSCMAKE nie rejestruje wszystkie symbole, które są zdefiniowane, ale nie odwołuje się. Jeśli spakowany plik .sbr ta opcja nie obowiązuje dla tego pliku wejściowego, ponieważ kompilator został już usunięty symbole bez odwołań.

**/n**<br/>
Wymusza nieprzyrostowa kompilacji. Użyj **/n** wymusić pełna kompilacja pliku informacyjnego przeglądarki, czy istnieje plik .bsc i uniemożliwić plików SBR obcinania. Zobacz [w jaki sposób BSCMAKE kompiluje plik .bsc](how-bscmake-builds-a-dot-bsc-file.md).

**/NOLOGO**<br/>
Pomija komunikat o prawach autorskich BSCMAKE.

**/o** *nazwy pliku*<br/>
Określa nazwę pliku informacyjnego przeglądarki. Domyślnie BSCMAKE zapewnia pliku informacyjnego przeglądarki podstawowej nazwy pierwszy plik SBR i rozszerzenie .bsc.

**/S (** *filename*... **)**<br/>
Informuje BSCMAKE do przetwarzania określonegop dołączanego pliku przy pierwszym napotkaniu go, a w celu wykluczenia go w przeciwnym razie. Użyj tej opcji, aby skrócić czas przetwarzania po pliku (np. nagłówka lub .h, pliku dla plików .c lub pliku źródłowego .cpp) znajduje się w kilku plikach źródłowych, ale nie ma wpływu dyrektywy przetwarzania wstępnego każdorazowo. Można również używać tej opcji, jeśli zmiany w pliku w sposób, który nie są ważne dla pliku informacyjnego przeglądarki, które tworzysz. Do określenia wielu plików, nazwy należy oddzielić spacjami i ująć listę w nawiasach. Nawiasy nie są konieczne, jeśli określisz tylko jeden *filename*. Jeśli chcesz wykluczyć plik za każdym razem, gdy zostało ono dołączone, należy użyć **/Ei** lub **/Es** opcji.

**/v**<br/>
Zapewnia pełne dane wyjściowe, która zawiera nazwę każdego pliku SBR, przetwarzane i informacji na temat BSCMAKE ukończone, uruchom.

**/?**<br/>
Wyświetla krótkie podsumowanie składni wiersza polecenia BSCMAKE.

Następujące polecenie w wierszu informuje BSCMAKE celu pełna kompilacja MAIN.bsc z trzech plików SBR. Informuje on BSCMAKE, które mają zostać wykluczone zduplikowane wystąpienia TOOLBOX.h:

```
BSCMAKE /n /S toolbox.h /o main.bsc file1.sbr file2.sbr file3.sbr
```

## <a name="see-also"></a>Zobacz także

[BSCMAKE — dokumentacja](bscmake-reference.md)
