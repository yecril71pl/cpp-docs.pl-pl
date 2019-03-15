---
title: /EXPORT (Eksportuje funkcję)
ms.date: 09/05/2018
f1_keywords:
- VC.Project.VCLinkerTool.ExportFunctions
- /export
helpviewer_keywords:
- /EXPORT linker option
- EXPORT linker option
- -EXPORT linker option
ms.assetid: 0920fb44-a472-4091-a8e6-73051f494ca0
ms.openlocfilehash: 7c4f4621bbccd4285bcf4eca07d2544d53d14f6c
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57819857"
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

1. [EKSPORTY](exports.md) instrukcja w pliku .def

1. Specyfikacji/Export, za pomocą polecenia łącza

1. A [komentarz](../../preprocessor/comment-c-cpp.md) dyrektywę w kodzie źródłowym w postaci `#pragma comment(linker, "/export: definition ")`.

Wszystkie te metody może służyć w tym samym programie. Gdy łącze tworzy program, który zawiera eksporty, tworzy również biblioteki importowanej, chyba że używany jest plik .exp w kompilacji.

Zastosowań łącze dekorowane formularzy identyfikatorów. Podczas tworzenia pliku .obj, kompilator zdobi identyfikatora. Jeśli *Nazwa_wpisu* określono konsolidatora w jego niedekorowanego formularza (wyświetlaną w kodzie źródłowym), łącze podejmuje próbę dopasowania nazwy. Nie można znaleźć unikatowego dopasowania, łącze wysyła komunikat o błędzie. Użyj [DUMPBIN](dumpbin-reference.md) narzędzie, aby uzyskać [nazwy ozdobionej](decorated-names.md) formularz identyfikator, gdy należy określić go do konsolidatora.

> [!NOTE]
> Nie określaj ozdobione formularza identyfikatory w języku C, które są zadeklarowane `__cdecl` lub `__stdcall`.

Jeśli potrzebujesz eksportować nazwy funkcji bez i eksportuje różne w zależności od konfiguracji kompilacji (na przykład w wersjach 32-bitową lub 64-bitowy), można użyć różnych plików DEF dla każdej konfiguracji. (Dyrektywy preprocesora warunkowego nie są dozwolone w pliki DEF). Alternatywnie, można użyć `#pragma comment` dyrektywy przed deklaracji funkcji, jak pokazano poniżej, gdzie `PlainFuncName` jest nieozdobioną nazwę i `_PlainFuncName@4` jest dekorowane nazwy funkcji:

```cpp
#pragma comment(linker, "/export:PlainFuncName=_PlainFuncName@4")
BOOL CALLBACK PlainFuncName( Things * lpParams)
```

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [kompilatora i tworzenia właściwości ustaw C++ w programie Visual Studio](../working-with-project-properties.md).

1. Wybierz **właściwości konfiguracji** > **konsolidatora** > **wiersza polecenia** stronę właściwości.

1. Wprowadź opcje do **dodatkowe opcje** pole.

### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Zobacz także

[Odwołania konsolidatora MSVC](linking.md)<br/>
[Opcje konsolidatora MSVC](linker-options.md)
