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
ms.openlocfilehash: a55b2a4ce72de644fe426894ab389f62bd29b204
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87232693"
---
# <a name="export-exports-a-function"></a>/EXPORT (Eksportuje funkcję)

Eksportuje funkcję według nazwy lub liczby porządkowej lub danych z programu.

## <a name="syntax"></a>Składnia

> **/Export:**<em>EntryName</em>[**, \@ **<em>porządkowa</em>[**, NoName**]] [**, dane**]

## <a name="remarks"></a>Uwagi

Opcja **/Export** określa funkcję lub element danych do wyeksportowania z programu, tak aby inne programy mogły wywołać funkcję lub użyć danych. Eksporty są zwykle zdefiniowane w bibliotece DLL.

*EntryName* jest nazwą funkcji lub elementu danych, która ma być używana przez program wywołujący. *numer porządkowy* Określa indeks w tabeli eksportu z zakresu od 1 do 65 535; Jeśli nie określisz *liczby porządkowej*, link przypisze jeden. Słowo kluczowe **NoName** eksportuje funkcję tylko jako numer porządkowy bez *wpisu*.

Słowo kluczowe **danych** określa, że wyeksportowany element jest elementem danych. Element danych w programie klienckim musi być zadeklarowany za pomocą **__declspec extern (dllimport)**.

Istnieją cztery metody eksportowania definicji, wymienione w zalecanej kolejności użycia:

1. [__declspec (dllexport)](../../cpp/dllexport-dllimport.md) w kodzie źródłowym

1. Instrukcja [eksportu](exports.md) w pliku. def

1. Specyfikacja/EXPORT w poleceniu LINKu

1. Dyrektywa [komentarza](../../preprocessor/comment-c-cpp.md) w kodzie źródłowym formularza `#pragma comment(linker, "/export: definition ")` .

Wszystkie te metody mogą być używane w tym samym programie. Gdy LINK kompiluje program, który zawiera eksporty, tworzy również bibliotekę importowaną, chyba że plik EXP jest używany w kompilacji.

LINK używa dekoracyjnych formularzy identyfikatorów. Kompilator zdobi identyfikator podczas tworzenia pliku. obj. Jeśli *EntryName* jest określony dla konsolidatora w postaci niedekoracyjnej (jak pojawia się w kodzie źródłowym), link próbuje dopasować nazwę. Jeśli nie można znaleźć unikatowego dopasowania, LINK wysyła komunikat o błędzie. Użyj narzędzia [polecenia DUMPBIN](dumpbin-reference.md) , aby uzyskać postać [nazwy dekoracyjnej](decorated-names.md) identyfikatora, gdy trzeba ją określić dla konsolidatora.

> [!NOTE]
> Nie określaj dekoracyjnej postaci identyfikatorów języka C, które są zadeklarowane **`__cdecl`** lub **`__stdcall`** .

Jeśli musisz wyeksportować niedekoracyjną nazwę funkcji i mieć różne Eksporty w zależności od konfiguracji kompilacji (na przykład w 32-bitowych lub 64-bitowych kompilacjach), możesz użyć różnych DEF plików dla każdej konfiguracji. (Dyrektywy warunkowe preprocesora są niedozwolone w plikach DEF). Alternatywnie można użyć `#pragma comment` dyrektywy przed deklaracją funkcji, jak pokazano w tym miejscu, gdzie `PlainFuncName` jest nazwą niedekoracyjną i `_PlainFuncName@4` jest nazwą dekoracyjną funkcji:

```cpp
#pragma comment(linker, "/export:PlainFuncName=_PlainFuncName@4")
BOOL CALLBACK PlainFuncName( Things * lpParams)
```

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio

1. Otwórz okno dialogowe **strony właściwości** projektu. Aby uzyskać szczegółowe informacje, zobacz [Ustawianie kompilatora C++ i właściwości kompilacji w programie Visual Studio](../working-with-project-properties.md).

1. Wybierz stronę właściwości **Konfiguracja właściwości**  >  **Linker**  >  **wiersza polecenia** konsolidatora.

1. Wprowadź opcję w polu **dodatkowe opcje** .

### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora

- Zobacz: <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Zobacz także

[Dokumentacja konsolidatora MSVC](linking.md)<br/>
[MSVC Opcje konsolidatora](linker-options.md)
