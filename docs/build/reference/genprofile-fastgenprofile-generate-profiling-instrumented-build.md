---
title: / Opcję GENPROFILE, /FASTGENPROFILE (Generuj profilowania kompilacji Instrumentowanej) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 03/14/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- GENPROFILE
- FASTGENPROFILE
- /GENPROFILE
- /FASTGENPROFILE
helpviewer_keywords:
- GENPROFILE
- FASTGENPROFILE
ms.assetid: deff5ce7-46f5-448a-b9cd-a7a83a6864c6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 05d7961ff46661b8f6df2768591932699c3965d4
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32379305"
---
# <a name="genprofile-fastgenprofile-generate-profiling-instrumented-build"></a>/ Opcję GENPROFILE, /FASTGENPROFILE (Generuj profilowania Instrumentowanej kompilacji)

Określa Generowanie pliku .pgd przez konsolidator, aby obsługiwać Optymalizacja sterowana profilem — (PGO). **/ Opcję GENPROFILE** i **/FASTGENPROFILE** różne domyślne parametry. Użyj **opcji/genprofile** preferować dokładności nad użyciem szybkość i pamięci podczas profilowania. Użyj **/FASTGENPROFILE** preferować mniejsze zużycie pamięci i szybkość nad dokładności.

## <a name="syntax"></a>Składnia

> **/GENPROFILE**[**:**{[**COUNTER32**|**COUNTER64**]|[**EXACT**|**NOEXACT**]|**MEMMAX=**_#_|**MEMMIN=**_#_|[**PATH**|**NOPATH** ]|[**TRACKEH** |**NOTRACKEH** ]|**PGD=**_filename_}]<br/>
> **/FASTGENPROFILE**[**:**{[**COUNTER32**|**COUNTER64**]|[**EXACT**|**NOEXACT**]|**MEMMAX=**_#_|**MEMMIN=**_#_|[**PATH**|**NOPATH** ]|[**TRACKEH** |**NOTRACKEH** ]|**PGD=**_filename_}]

### <a name="arguments"></a>Argumenty

Można określić jedną z następujących argumentów, aby **opcji/genprofile** lub **/FASTGENPROFILE**. Argumenty wymienione w tym miejscu rozdzielone znakiem kreski pionowej (**|**) znaków wzajemnie się wykluczają. Użyj przecinka (**,**) znak oddzielający opcje.

**COUNTER32** &AMP;#124; **COUNTER64**<br/>
Użyj **COUNTER32** stosowanie liczniki sondowania 32-bitowe i **COUNTER64** do określenia liczniki sondowania 64-bitowych. Po określeniu **opcji/genprofile**, wartość domyślna to **COUNTER64**. Po określeniu **/FASTGENPROFILE**, wartość domyślna to **COUNTER32**.

**DOKŁADNE** &AMP;#124; **NOEXACT**<br/>
Użyj **EXACT** do określenia wątkowo zwiększa blokowanego dla sondy. **NOEXACT** Określa przyrost niechronione operacje dla sondy. Wartość domyślna to **NOEXACT**.

**MEMMAX**=*wartość*, **MEMMIN**=*wartości*<br/>
Użyj **MEMMAX** i **MEMMIN** do określania rozmiarów minimalnego i maksymalnego rezerwacji danych szkoleniowych w pamięci. Wartość to ilość pamięci do zarezerwowania w bajtach. Domyślnie te wartości są określane przez wewnętrzny heurystycznego.

**ŚCIEŻKA** &AMP;#124; **NOPATH**  <br/>
Użyj **ścieżki** określić osobny zestaw liczników PGO dla każdej unikatowej ścieżki do funkcji. Użyj **NOPATH** można określić tylko jeden zestaw liczników dla każdej funkcji. Po określeniu **opcji/genprofile**, wartość domyślna to **ścieżki** . Po określeniu **/FASTGENPROFILE**, wartość domyślna to **NOPATH** .

**TRACKEH** &AMP;#124; **NOTRACKEH** <br/>
Określa, czy zachować dokładne liczby, gdy wyjątki zostaną zgłoszone podczas uczenia przy użyciu dodatkowych liczników. Użyj **TRACKEH** Aby określić dodatkowe liczniki dokładne Count. Użyj **NOTRACKEH** do określenia pojedynczego liczniki dla kodu, który nie korzysta z wyjątkiem obsługi lub że nie występują wyjątków w Twojej scenariusze szkoleniowe.  Po określeniu **opcji/genprofile**, wartość domyślna to **TRACKEH** . Po określeniu **/FASTGENPROFILE**, wartość domyślna to **NOTRACKEH** .

**PGD**=*filename*<br/>
Określa nazwę pliku podstawowego plik .pgd. Domyślnie konsolidator używa nazwy pliku obrazu podstawowego pliku wykonywalnego z rozszerzeniem .pgd.

## <a name="remarks"></a>Uwagi

**Opcji/genprofile** i **/FASTGENPROFILE** opcje Poinformuj konsolidator, aby wygenerować profilowania pliku Instrumentacji potrzebnych do obsługi aplikacji szkoleń dla optymalizacji sterowanych profilem (PGO). Te opcje są nowością w programie Visual Studio 2015. Te opcje, aby przestarzałe preferowane **/LTCG:PGINSTRUMENT**, **/PGD** i **/POGOSAFEMODE** opcje i **PogoSafeMode**,  **Vcprofile_alloc_scale —** i **VCPROFILE_PATH** zmiennych środowiskowych. Informacje dotyczące profilowania generowane przez szkolenia aplikacji jest używany jako dane wejściowe do wykonania docelowe optymalizacji całego programu podczas kompilacji. Można ustawić dodatkowe opcje do kontrolowania różnych funkcji profilowania wydajności podczas uczenia aplikacji i tworzy. Domyślne opcje określone przez **opcji/genprofile** zwrócić wyników najbardziej dokładna, zwłaszcza w przypadku dużych, złożonych aplikacji wielowątkowych. **/FASTGENPROFILE** opcja używa różne ustawienia domyślne niższe zużycie pamięci i zwiększyć wydajność podczas uczenia kosztem dokładności.

Informacje dotyczące profilowania jest przechwytywany po uruchomieniu instrumentowanego aplikacji po utworzeniu za pomocą **opcji/genprofile** z **/FASTGENPROFILE**. Te informacje są przechwytywane po określeniu [/USEPROFILE](useprofile.md) — opcja konsolidatora do wykonania profilowania kroku i następnie używany do przewodnika krok optymalizowania kompilacji. Więcej informacji na temat sposobu uczenia aplikacji i uzyskać szczegółowe informacje dotyczące zebranych danych, zobacz [profilowana Optymalizacja](profile-guided-optimizations.md).

Należy także określić **opcję/LTCG** po określeniu **opcji/genprofile** lub **/FASTGENPROFILE**.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio

1. Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Ustawianie właściwości projektu Visual C++](../../ide/working-with-project-properties.md).

1. Wybierz **właściwości konfiguracji** > **konsolidatora** > **wiersza polecenia** strony właściwości.

1. Wprowadź **opcji/genprofile** lub **/FASTGENPROFILE** opcje i argumenty do **dodatkowe opcje** pole. Wybierz **OK** Aby zapisać zmiany.

### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Zobacz także

[Ustawianie opcji konsolidatora](../../build/reference/setting-linker-options.md)<br/>
[Opcje konsolidatora](../../build/reference/linker-options.md)<br/>
[/LTCG (Generowanie łączonych kodów czasowych)](../../build/reference/ltcg-link-time-code-generation.md)<br/>
