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
ms.openlocfilehash: 5063eae507ee6c83cbed2ae7fc92679098b91f36
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44104622"
---
# <a name="export-exports-a-function"></a>/EXPORT (Eksportuje funkcję)

Eksportuje funkcję według nazwy lub numer lub danych z programu.

## <a name="syntax"></a>Składnia

> **/ EXPORT:**<em>Nazwa_wpisu</em>[**,\@**<em>porządkowe</em>[**, NONAME**]] [**, dane**]

## <a name="remarks"></a>Uwagi

**/EXPORT** opcja określa element funkcję lub dane, aby wyeksportować z programu, tak aby inne programy można wywołać funkcję lub korzystać z danych. Eksporty są zazwyczaj zdefiniowane w bibliotece DLL.

*Nazwa_wpisu* jest nazwa elementu funkcję lub dane, ponieważ jest używane przez program wywołujący. *numer porządkowy* Określa indeks w tabeli eksportu do zakresu od 1 do 65 535; Jeśli nie określisz *porządkowe*, LINK przypisuje jeden. **NONAME** — słowo kluczowe eksportuje funkcję tylko jako liczby porządkowej, bez *Nazwa_wpisu*.

**Danych** — słowo kluczowe Określa, że element wyeksportowanego elementu danych. Element danych w programie klienckim musi być zadeklarowany za pomocą **extern __declspec(dllimport)**.

Istnieją cztery metody eksportowania definicji, wymienione w zalecanej kolejności używania:

1. [__declspec(dllexport)](../../cpp/dllexport-dllimport.md) w kodzie źródłowym

1. [EKSPORTY](../../build/reference/exports.md) instrukcja w pliku .def

1. Specyfikacji/Export, za pomocą polecenia łącza

1. A [komentarz](../../preprocessor/comment-c-cpp.md) dyrektywę w kodzie źródłowym w postaci `#pragma comment(linker, "/export: definition ")`.

Wszystkie te metody może służyć w tym samym programie. Gdy łącze tworzy program, który zawiera eksporty, tworzy również biblioteki importowanej, chyba że używany jest plik .exp w kompilacji.

Zastosowań łącze dekorowane formularzy identyfikatorów. Podczas tworzenia pliku .obj, kompilator zdobi identyfikatora. Jeśli *Nazwa_wpisu* określono konsolidatora w jego niedekorowanego formularza (wyświetlaną w kodzie źródłowym), łącze podejmuje próbę dopasowania nazwy. Nie można znaleźć unikatowego dopasowania, łącze wysyła komunikat o błędzie. Użyj [DUMPBIN](../../build/reference/dumpbin-reference.md) narzędzie, aby uzyskać [nazwy ozdobionej](../../build/reference/decorated-names.md) formularz identyfikator, gdy należy określić go do konsolidatora.

> [!NOTE]
> Nie określaj ozdobione formularza identyfikatory w języku C, które są zadeklarowane `__cdecl` lub `__stdcall`.

Jeśli potrzebujesz eksportować nazwy funkcji bez i eksportuje różne w zależności od konfiguracji kompilacji (na przykład w wersjach 32-bitową lub 64-bitowy), można użyć różnych plików DEF dla każdej konfiguracji. (Dyrektywy preprocesora warunkowego nie są dozwolone w pliki DEF). Alternatywnie, można użyć `#pragma comment` dyrektywy przed deklaracji funkcji, jak pokazano poniżej, gdzie `PlainFuncName` jest nieozdobioną nazwę i `_PlainFuncName@4` jest dekorowane nazwy funkcji:

```cpp
#pragma comment(linker, "/export:PlainFuncName=_PlainFuncName@4")
BOOL CALLBACK PlainFuncName( Things * lpParams)
```

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [ustawienie właściwości projektu Visual C++](../../ide/working-with-project-properties.md).

2. Wybierz **właściwości konfiguracji** > **konsolidatora** > **wiersza polecenia** stronę właściwości.

3. Wprowadź opcje do **dodatkowe opcje** pole.

### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Zobacz też

[Ustawianie opcji konsolidatora](../../build/reference/setting-linker-options.md)   
[Opcje konsolidatora](../../build/reference/linker-options.md)
