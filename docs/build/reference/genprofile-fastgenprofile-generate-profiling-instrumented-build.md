---
title: / GENPROFILE, / fastgenprofile (Generuj kompilację Instrumentowaną profilowaniem)
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
ms.openlocfilehash: cf6327b175344f1e2914792eb47a4838e544ea24
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57813880"
---
# <a name="genprofile-fastgenprofile-generate-profiling-instrumented-build"></a>/ GENPROFILE, / fastgenprofile (Generuj kompilację Instrumentowaną profilowaniem)

Określa Generowanie pliku .pgd przez konsolidator, aby obsługiwać profilowana Optymalizacja (PGO). **/ GENPROFILE** i **/fastgenprofile** różne domyślne parametry. Użyj **przełączników/genprofile** preferować dokładności za pośrednictwem prędkości oraz użycia pamięci podczas profilowania. Użyj **/fastgenprofile** aby preferował mniejsze zużycie pamięci i szybkość nad dokładności.

## <a name="syntax"></a>Składnia

> **/GENPROFILE**[**:**{[**COUNTER32**|**COUNTER64**]|[**EXACT**|**NOEXACT**]|**MEMMAX=**_#_|**MEMMIN=**_#_|[**PATH**|**NOPATH** ]|[**TRACKEH** |**NOTRACKEH** ]|**PGD=**_filename_}]<br/>
> **/FASTGENPROFILE**[**:**{[**COUNTER32**|**COUNTER64**]|[**EXACT**|**NOEXACT**]|**MEMMAX=**_#_|**MEMMIN=**_#_|[**PATH**|**NOPATH** ]|[**TRACKEH** |**NOTRACKEH** ]|**PGD=**_filename_}]

### <a name="arguments"></a>Argumenty

Można określić dowolny z następujących argumentów, aby **przełączników/genprofile** lub **/fastgenprofile**. Na liście argumentów rozdzielonych znakiem kreski pionowej (**|**) znak wzajemnie się wykluczają. Należy użyć przecinka (**,**) znak oddzielający opcje.

**WARTOŚĆ COUNTER32** &AMP;#124; **COUNTER64**<br/>
Użyj **wartość COUNTER32** stosowanie liczniki sondy 32-bitowe i **COUNTER64** do określenia liczniki sondy 64-bitowych. Po określeniu **przełączników/genprofile**, wartość domyślna to **COUNTER64**. Po określeniu **/fastgenprofile**, wartość domyślna to **wartość COUNTER32**.

**DOKŁADNE** &AMP;#124; **NOEXACT**<br/>
Użyj **EXACT** do określenia wątkowo przyrosty blokowane dla sondy. **NOEXACT** określa operacje inkrementacji niechronione dla sondy. Wartość domyślna to **NOEXACT**.

**MEMMAX**=*value*, **MEMMIN**=*value*<br/>
Użyj **MEMMAX** i **MEMMIN** Aby określić rozmiary rezerwacji maksymalne i minimalne dane szkoleniowe w pamięci. Wartość jest ilość pamięci do zarezerwowania w bajtach. Domyślnie te wartości są określane przez wewnętrzny heurystyki.

**PATH**  &#124; **NOPATH** <br/>
Użyj **ścieżki** do określenia oddzielny zestaw liczników PGO dla każdego unikatową ścieżkę do funkcji. Użyj **NOPATH** można określić tylko jeden zestaw liczników dla każdej funkcji. Po określeniu **przełączników/genprofile**, wartość domyślna to **ścieżki** . Po określeniu **/fastgenprofile**, wartość domyślna to **NOPATH** .

**TRACKEH**  &#124; **NOTRACKEH** <br/>
Określa, czy zachować dokładne liczby, gdy wyjątki zostaną zgłoszone podczas szkolenia za pomocą dodatkowych liczników. Użyj **TRACKEH** Aby określić dodatkowe liczniki dokładna liczba. Użyj **NOTRACKEH** do określenia pojedynczego liczniki dla kodu, który nie korzysta z wyjątkiem obsługi lub które nie napotka wyjątków w swoich scenariuszy szkoleniowych.  Po określeniu **przełączników/genprofile**, wartość domyślna to **TRACKEH** . Po określeniu **/fastgenprofile**, wartość domyślna to **NOTRACKEH** .

**Plik PGD**=*nazwy pliku*<br/>
Określa nazwę pliku podstawowego pliku .pgd. Domyślnie konsolidator używa nazwy pliku obrazu podstawowego pliku wykonywalnego z rozszerzeniem .pgd.

## <a name="remarks"></a>Uwagi

**Przełączników/genprofile** i **/fastgenprofile** opcje stwierdzić, konsolidator generuje plik profilowania Instrumentacji potrzebnych do obsługi aplikacji szkolenia dla profilowana Optymalizacja (PGO). Te opcje są nowością w programie Visual Studio 2015. Preferuj tych opcji do przestarzałej **pginstrument**, **/PGD** i **/POGOSAFEMODE** opcje i **PogoSafeMode**,  **Vcprofile_alloc_scale —** i **vcprofile_path jest** zmiennych środowiskowych. Dane profilowania wygenerowane przez aplikację szkolenia jest używany jako dane wejściowe do wykonania docelowe optymalizacji całego programu podczas kompilacji. Można ustawić dodatkowe opcje do kontrolowania różnych funkcji profilowania wydajności podczas uczenia aplikacji i kompilacji. Domyślne opcje określone przez **przełączników/genprofile** zapewniają najbardziej dokładne wyniki, szczególnie w przypadku dużych, złożonych aplikacji wielowątkowych. **/Fastgenprofile** opcja przy użyciu różnych wartości domyślne dla mniejsze obciążenie pamięci i zwiększyć wydajność podczas szkolenia, kosztem dokładności.

Informacje profilowania są przechwytywane, po uruchomieniu instrumentowanego aplikacji po skompilowaniu przy użyciu **przełączników/genprofile** z **/fastgenprofile**. Te informacje są przechwytywane podczas określania [/USEPROFILE](useprofile.md) — opcja konsolidatora przeprowadzić profilowanie kroku i następnie używany do przewodnika krok optymalizowania kompilacji. Więcej informacji na temat to w opracowywaniu aplikacji i szczegółowe informacje na temat zebranych danych, zobacz [optymalizacje Profile-Guided](../profile-guided-optimizations.md).

Należy także określić **opcję/LTCG** po określeniu **przełączników/genprofile** lub **/fastgenprofile**.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [kompilatora i tworzenia właściwości ustaw C++ w programie Visual Studio](../working-with-project-properties.md).

1. Wybierz **właściwości konfiguracji** > **konsolidatora** > **wiersza polecenia** stronę właściwości.

1. Wprowadź **przełączników/genprofile** lub **/fastgenprofile** opcje i argumenty do **dodatkowe opcje** pole. Wybierz **OK** Aby zapisać zmiany.

### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Zobacz także

[Odwołania konsolidatora MSVC](linking.md)<br/>
[Opcje konsolidatora MSVC](linker-options.md)<br/>
[/LTCG (Generowanie łączonych kodów czasowych)](ltcg-link-time-code-generation.md)<br/>
