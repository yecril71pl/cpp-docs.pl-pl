---
title: /GENPROFILE, /FASTGENPROFILE (Generuj kompilację instrumentowaną profilowaniem)
ms.date: 03/14/2018
f1_keywords:
- GENPROFILE
- FASTGENPROFILE
- /GENPROFILE
- /FASTGENPROFILE
helpviewer_keywords:
- GENPROFILE
- FASTGENPROFILE
ms.assetid: deff5ce7-46f5-448a-b9cd-a7a83a6864c6
ms.openlocfilehash: 19ddf56d92cc2d8fbbfaf635c8e1602443e35b5b
ms.sourcegitcommit: 6b749db14b4cf3a2b8d581fda6fdd8cb98bc3207
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/05/2020
ms.locfileid: "82825792"
---
# <a name="genprofile-fastgenprofile-generate-profiling-instrumented-build"></a>/GENPROFILE, /FASTGENPROFILE (Generuj kompilację instrumentowaną profilowaniem)

Określa generowanie pliku. PGD przez konsolidator do obsługi optymalizacji opartej na profilach (PGO). **/GENPROFILE** i **/FASTGENPROFILE** używają różnych parametrów domyślnych. Użyj **/GENPROFILE** , aby preferować precyzję użycia szybkości i pamięci podczas profilowania. Użyj **/FASTGENPROFILE** , aby zwiększyć użycie pamięci i szybkość z dokładnością.

## <a name="syntax"></a>Składnia

> **/GENPROFILE**[**:**{[**COUNTER32**|**COUNTER64**] | [ **dokładne**|**noexact**] | **MEMMAX =**_#_|**MEMMIN =**_#_| [**ścieżka**|**nopath** ] | [**TRACKEH** |**NOTRACKEH** ] | **PGD =**_Nazwa pliku_}] \
> **/FASTGENPROFILE**[**:**{[**COUNTER32**|**COUNTER64**] | [ **dokładne**|**noexact**] | **MEMMAX =**_#_|**MEMMIN =**_#_| [**ścieżka**|**nopath** ] | [**TRACKEH** |**NOTRACKEH** ] | **PGD =**_Nazwa pliku_}]

### <a name="arguments"></a>Argumenty

Dowolny z następujących argumentów można określić jako **/GENPROFILE** lub **/FASTGENPROFILE**. Argumenty wymienione tutaj oddzielone znakiem potoku (**|**) wykluczają się wzajemnie. Użyj znaku przecinka (**,**), aby oddzielić opcje.

**COUNTER32** &#124; **COUNTER64**<br/>
Użyj **COUNTER32** , aby określić użycie 32-bitowych liczników sond i **COUNTER64** , aby określić 64-bitowe liczniki sond. Po określeniu **/GENPROFILE**wartość domyślna to **COUNTER64**. Po określeniu **/FASTGENPROFILE**wartość domyślna to **COUNTER32**.

**Dokładne** &#124; **noexact**<br/>
Użyj **dokładnej** , aby określić, które są Zablokowani z bezpiecznymi wątkami dla sond. **Noexact** określa niechronione operacje przyrostu dla sond. Wartość domyślna to **noexact**.

**MEMMAX**=*Wartość*MEMMAX, **MEMMIN**=*wartość*<br/>
Użyj **MEMMAX** i **MEMMIN** , aby określić maksymalne i minimalne rozmiary rezerwacji dla danych szkoleniowych w pamięci. Wartość jest ilością pamięci do zarezerwowania w bajtach. Domyślnie te wartości są określane przez wewnętrzny algorytm heurystyczny.

**Ścieżka** &#124; **nopath** <br/>
Użyj **ścieżki** , aby określić oddzielny zestaw PGO liczników dla każdej unikatowej ścieżki do funkcji. Użyj **nopath** , aby określić tylko jeden zestaw liczników dla każdej funkcji. Po określeniu **/GENPROFILE**, wartość domyślna to **Path** . Po określeniu **/FASTGENPROFILE**wartość domyślna to **nopath** .

**TRACKEH** &#124; **NOTRACKEH** <br/>
Określa, czy należy używać dodatkowych liczników, aby zachować dokładną liczbę wyjątków, gdy podczas uczenia zostaną zgłoszone wyjątki. Użyj **TRACKEH** , aby określić dodatkowe liczniki dla dokładnej liczby. Użyj **NOTRACKEH** , aby określić pojedyncze liczniki dla kodu, który nie korzysta z obsługi wyjątków lub nie napotyka wyjątków w scenariuszach szkoleniowych.  Po określeniu **/GENPROFILE**wartość domyślna to **TRACKEH** . Po określeniu **/FASTGENPROFILE**wartość domyślna to **NOTRACKEH** .

**PGD**=*Nazwa pliku* PGD<br/>
Określa podstawową nazwę pliku. pgd. Domyślnie konsolidator używa podstawowej nazwy pliku obrazu wykonywalnego z rozszerzeniem. pgd.

## <a name="remarks"></a>Uwagi

Opcje **/GENPROFILE** i **/FASTGENPROFILE** umożliwiają konsolidatorowi wygenerowanie pliku instrumentacji profilowania wymaganego do obsługi szkoleń aplikacji dla optymalizacji opartej na profilach (PGO). Te opcje są nowe w programie Visual Studio 2015. Należy preferować te opcje do przestarzałych opcji **/LTCG: PGINSTRUMENT**, **/PGD** i **/POGOSAFEMODE** oraz zmiennych środowiskowych **POGOSAFEMODE**, **VCPROFILE_ALLOC_SCALE** i **VCPROFILE_PATH** . Informacje profilowania wygenerowane przez szkolenie aplikacji są używane jako dane wejściowe do przeprowadzania przeszukiwanych całych programów podczas kompilacji. Można ustawić dodatkowe opcje sterujące różnymi funkcjami profilowania dla wydajności podczas szkoleń i kompilacji aplikacji. Domyślne opcje określone przez **/GENPROFILE** zapewniają najbardziej dokładne wyniki, szczególnie w przypadku dużych, złożonych aplikacji wielowątkowych. Opcja **/FASTGENPROFILE** używa różnych wartości domyślnych dla mniejszej ilości pamięci i wydajności podczas uczenia się, kosztem dokładności.

Informacje profilowania są przechwytywane po uruchomieniu aplikacji z instrumentacją po skompilowaniu przy użyciu **/GENPROFILE** of **/FASTGENPROFILE**. Te informacje są przechwytywane po określeniu opcji konsolidatora [/USEPROFILE](useprofile.md) , aby wykonać krok profilowania, a następnie użyć do przeprowadzenia optymalizacji zoptymalizowanego kroku kompilacji. Aby uzyskać więcej informacji na temat uczenia aplikacji i szczegółów dotyczących zebranych danych, zobacz [optymalizacje profilowe](../profile-guided-optimizations.md).

Należy również określić **/LTCG** podczas określania **/GENPROFILE** lub **/FASTGENPROFILE**.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio

1. Otwórz okno dialogowe **strony właściwości** projektu. Aby uzyskać szczegółowe informacje, zobacz [Ustawianie kompilatora C++ i właściwości kompilacji w programie Visual Studio](../working-with-project-properties.md).

1. Wybierz stronę właściwości **Konfiguracja właściwości** > **wiersza polecenia** **konsolidatora** > .

1. Wprowadź opcje **/GENPROFILE** lub **/FASTGENPROFILE** i argumenty w polu **dodatkowe opcje** . Wybierz **przycisk OK** , aby zapisać zmiany.

### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora

- Zobacz: <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Zobacz także

[Dokumentacja konsolidatora MSVC](linking.md)<br/>
[Opcje konsolidatora MSVC](linker-options.md)<br/>
[/LTCG (Generowanie łączonych kodów czasowych)](ltcg-link-time-code-generation.md)<br/>
