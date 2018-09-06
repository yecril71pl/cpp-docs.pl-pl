---
title: -EXPORT (Eksportuje funkcję) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/05/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.ExportFunctions
- /export
dev_langs:
- C++
helpviewer_keywords:
- /EXPORT linker option
- EXPORT linker option
- -EXPORT linker option
ms.assetid: 0920fb44-a472-4091-a8e6-73051f494ca0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 16ec6be15635ebfc085615015b1221231645970d
ms.sourcegitcommit: d10a2382832373b900b1780e1190ab104175397f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "43894797"
---
# <a name="export-exports-a-function"></a>/EXPORT (Eksportuje funkcję)

Eksportuje funkcję według nazwy lub numer lub danych z programu.

## <a name="syntax"></a>Składnia

> **/ EXPORT:**<em>Nazwa_wpisu</em>[**,\@**<em>porządkowe</em>[**, NONAME**]] [**, dane**]

## <a name="remarks"></a>Uwagi

Z opcją/Export funkcji można eksportować z programu tak, aby inne programy mogą wywołać tę funkcję. Można także eksportować dane. Eksporty są zazwyczaj zdefiniowane w bibliotece DLL.

*Nazwa_wpisu* jest nazwa elementu funkcję lub dane, ponieważ jest używane przez program wywołujący. `ordinal` Określa indeks w tabeli eksportu do zakresu od 1 do 65 535; Jeśli nie określisz `ordinal`, LINK przypisuje jeden. **NONAME** — słowo kluczowe eksportuje funkcję tylko jako liczby porządkowej, bez *Nazwa_wpisu*.

**Danych** — słowo kluczowe Określa, że element wyeksportowanego elementu danych. Element danych w programie klienckim musi być zadeklarowany za pomocą **extern __declspec(dllimport)**.

Istnieją trzy metody eksportowania definicji, wymienione w zalecanej kolejności używania:

1. [__declspec(dllexport)](../../cpp/dllexport-dllimport.md) w kodzie źródłowym

2. [EKSPORTY](../../build/reference/exports.md) instrukcja w pliku .def

3. Specyfikacji/Export, za pomocą polecenia łącza

Wszystkie trzy metody może służyć w tym samym programie. Gdy łącze tworzy program, który zawiera eksporty, tworzy również biblioteki importowanej, chyba że używany jest plik .exp w kompilacji.

Zastosowań łącze dekorowane formularzy identyfikatorów. Podczas tworzenia pliku .obj, kompilator zdobi identyfikatora. Jeśli *Nazwa_wpisu* określono konsolidatora w jego niedekorowanego formularza (wyświetlaną w kodzie źródłowym), łącze podejmuje próbę dopasowania nazwy. Nie można znaleźć unikatowego dopasowania, łącze wysyła komunikat o błędzie. Użyj [DUMPBIN](../../build/reference/dumpbin-reference.md) narzędzie, aby uzyskać [nazwy dekorowane](../../build/reference/decorated-names.md) formularz identyfikator, gdy należy określić go do konsolidatora.

> [!NOTE]
> Nie określaj ozdobione formularza identyfikatory w języku C, które są zadeklarowane `__cdecl` lub `__stdcall`.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [ustawienie właściwości projektu Visual C++](../../ide/working-with-project-properties.md).

2. Wybierz **właściwości konfiguracji** > **konsolidatora** > **wiersza polecenia** stronę właściwości.

3. Wprowadź opcje do **dodatkowe opcje** pole.

### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Zobacz też

[Ustawianie opcji konsolidatora](../../build/reference/setting-linker-options.md)   
[Opcje konsolidatora](../../build/reference/linker-options.md)