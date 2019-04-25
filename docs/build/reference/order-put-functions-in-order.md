---
title: /ORDER (Ustaw funkcje w kolejności)
ms.date: 09/05/2018
f1_keywords:
- VC.Project.VCLinkerTool.FunctionOrder
- /order
helpviewer_keywords:
- ORDER linker option
- -ORDER linker option
- LINK tool [C++], program optimizing
- /ORDER linker option
- LINK tool [C++], swap tuning
- paging, optimizing
ms.assetid: ecf5eb3e-e404-4e86-9a91-4e5ec157261a
ms.openlocfilehash: b1927ffd2efc923157fe1956fe905c939bc62719
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62320191"
---
# <a name="order-put-functions-in-order"></a>/ORDER (Ustaw funkcje w kolejności)

Określ kolejność łączy oddzielnie spakowanych funkcji (COMDAT).

## <a name="syntax"></a>Składnia

> **/ ORDER:\@**<em>nazwy pliku</em>

### <a name="parameters"></a>Parametry

*Nazwa pliku*<br/>
Plik tekstowy, który określa kolejność łączy dla sekcji COMDAT funkcji.

## <a name="remarks"></a>Uwagi

**/ORDER** — opcja kompilatora pozwala zoptymalizować zachowanie stronicowania programu przez grupowanie funkcji wraz z funkcji wywoływanych przez nią. Często wywoływane funkcje można także grupować ze sobą. Te techniki, znane jako *dostrajanie swap* lub *optymalizacji stronicowania*, zwiększyć prawdopodobieństwo, że wywoływana funkcja jest w pamięci, gdy jest wymagana i nie ma być stronicowana z dysku.

Podczas kompilowania kodu źródłowego do pliku obiektu, można stwierdzić, kompilator, aby umieścić każdą funkcję w osobnej sekcji o nazwie *COMDAT*, za pomocą [/Gy (włączenie łączenia poziomie funkcji)](gy-enable-function-level-linking.md) kompilatora Opcja. **/ORDER** — opcja konsolidatora informuje konsolidator umieszcza Comdat w pliku wykonywalnego obrazu, w kolejności, można określić.

Aby określić kolejność sekcji COMDAT, należy utworzyć *pliku odpowiedzi*, plik tekstowy, który zawiera listę poszczególnych sekcji COMDAT według nazwy, jeden na wiersz, w kolejności, w jakiej mają być nawiązywane przez konsolidator. Przekaż nazwę tego pliku jako *filename* parametru **/ORDER** opcji. W przypadku funkcji C++ nazwę COMDAT jest formie dekorowane nazwy funkcji. Użyj nieozdobioną nazwę zawartej funkcji C `main`, a dla funkcji języka C++ jest zadeklarowany jako `extern "C"`. Nazwy i nazwy dekorowane uwzględniają wielkość liter. Aby uzyskać więcej informacji na temat nazwy dekorowane, zobacz [nazwy dekorowane](decorated-names.md).

Aby znaleźć uzupełnioną swoje Comdat, należy użyć [DUMPBIN](dumpbin-reference.md) narzędzia [/symbole](symbols.md) opcja w pliku obiektu. Konsolidator automatycznie dołącza znaku podkreślenia (**\_**) do funkcji nazwy w odpowiedzi plików, chyba, że nazwa zaczyna się od znaku zapytania (**?**) lub znak ( **\@**). Na przykład, jeśli plik źródłowy example.cpp, zawiera funkcje `int cpp_func(int)`, `extern "C" int c_func(int)` i `int main(void)`, polecenie `DUMPBIN /SYMBOLS example.obj` wyświetla te nazwy dekorowane:

```Output
...
088 00000000 SECT1A notype ()    External     | ?cpp_func@@YAHH@Z (int __cdecl cpp_func(int))
089 00000000 SECT22 notype ()    External     | _c_func
08A 00000000 SECT24 notype ()    External     | _main
...
```

W takim przypadku określić nazwy jako `?cpp_func@@YAHH@Z`, `c_func`, i `main` w pliku odpowiedzi.

Jeśli istnieje więcej niż jedna **/ORDER** opcja jest wyświetlana w obszarze Opcje konsolidatora, ostatni z nich określone staje się skuteczny.

**/ORDER** opcji wyłącza łączenie przyrostowe. Może zostać wyświetlony konsolidatora ostrzeżenie [LNK4075](../../error-messages/tool-errors/linker-tools-warning-lnk4075.md) po określeniu tę opcję, jeśli włączono łączenie przyrostowe lub jeśli określono [/zi (przyrostowe PDB)](z7-zi-zi-debug-information-format.md) — opcja kompilatora. Aby wyciszyć to ostrzeżenie, można użyć [/incremental: No](incremental-link-incrementally.md) — opcja konsolidatora wyłączyć przyrostowe konsolidowanie i używać [/zi (Generowanie pliku PDB)](z7-zi-zi-debug-information-format.md) opcję kompilatora, aby wygenerować pliku PDB bez konsolidacji przyrostowej.

> [!NOTE]
> ŁĄCZE nie zamówienia statyczne funkcje, ponieważ nazwy statycznej funkcji nie są nazwy symboli publicznych. Gdy **/ORDER** jest określona, konsolidator ostrzeżenie [LNK4037](../../error-messages/tool-errors/linker-tools-warning-lnk4037.md) jest generowany dla każdego symbolu w pliku odpowiedzi zamówienia, który jest statyczny lub nie został odnaleziony.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [kompilatora i tworzenia właściwości ustaw C++ w programie Visual Studio](../working-with-project-properties.md).

1. Wybierz **właściwości konfiguracji** > **konsolidatora** > **optymalizacji** stronę właściwości.

1. Modyfikowanie **kolejność funkcji** właściwości, aby zawierały nazwę pliku odpowiedzi.

### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.FunctionOrder%2A>.

## <a name="see-also"></a>Zobacz także

[Dokumentacja konsolidatora MSVC](linking.md)<br/>
[Opcje konsolidatora MSVC](linker-options.md)
