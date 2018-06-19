---
title: -ORDER (Ustaw funkcje w kolejności) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.FunctionOrder
- /order
dev_langs:
- C++
helpviewer_keywords:
- ORDER linker option
- -ORDER linker option
- LINK tool [C++], program optimizing
- /ORDER linker option
- LINK tool [C++], swap tuning
- paging, optimizing
ms.assetid: ecf5eb3e-e404-4e86-9a91-4e5ec157261a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: de9b0fb629a1bf984929ec170f05e25e740e9cd5
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32378486"
---
# <a name="order-put-functions-in-order"></a>/ORDER (Ustaw funkcje w kolejności)

Określ kolejność łączy oddzielnie spakowanych funkcji (COMDAT).

## <a name="syntax"></a>Składnia

>/ ORDER: @*filename*

### <a name="parameters"></a>Parametry

*Nazwa pliku*  
Plik tekstowy, który określa kolejność łącza do funkcji COMDAT.

## <a name="remarks"></a>Uwagi

**/Kolejność** — opcja kompilatora służy do optymalizacji zachowanie stronicowania programu grupując funkcja wraz z wywołaniem funkcji. Można także grupować funkcje często wywoływane ze sobą. Te techniki, znany jako *dostrajanie swap* lub *optymalizacji stronicowania*, zwiększyć prawdopodobieństwo, że wywoływana funkcja jest w pamięci, gdy są potrzebne i nie ma być stronicowana z dysku.

Podczas kompilowania kodu źródłowego w pliku obiektu, można określić, kompilator, aby umieścić poszczególnych funkcji w osobnej sekcji o nazwie *COMDAT*, za pomocą [/Gy (włączenie łączenia poziomie funkcji)](../../build/reference/gy-enable-function-level-linking.md) kompilatora Opcja. **/Kolejność** — opcja konsolidatora informuje konsolidator, aby umieścić Comdat w obrazu wykonywalnego w kolejności, można określić.

Aby określić kolejność COMDAT, Utwórz *pliku odpowiedzi*, plik tekstowy, który zawiera listę poszczególnych COMDAT według nazwy, po jednym dla każdego wiersza w kolejności, w jakiej mają być nawiązywane przez konsolidator. Przekaż nazwę tego pliku jako *filename* parametr **/kolejność** opcji. Dla funkcji języka C++ nazwa COMDAT jest ozdobione formę nazwę funkcji. Użyj bez nazwy dla funkcji języka C `main`, i dla funkcji języka C++ zadeklarowany jako `extern "C"`. Nazwy funkcji i nazwy ozdobione jest uwzględniana wielkość liter. Aby uzyskać więcej informacji o nazwach ozdobione, zobacz [dekorowane nazwy](../../build/reference/decorated-names.md). 

Aby znaleźć nazwy ozdobione Twojej Comdat, użyj [DUMPBIN](../../build/reference/dumpbin-reference.md) narzędzia [/symbole](../../build/reference/symbols.md) opcji w pliku obiektu. Konsolidator dołącza automatycznie znaku podkreślenia (\_) do funkcji nazwy w odpowiedzi plików chyba, że nazwa rozpoczyna się znakiem zapytania (?) lub znak @ (@). Na przykład, jeśli plik źródłowy example.cpp, zawiera funkcje `int cpp_func(int)`, `extern "C" int c_func(int)` i `int main(void)`, polecenie `DUMPBIN /SYMBOLS example.obj` wymieniono te nazwy ozdobione:

```Output
...
088 00000000 SECT1A notype ()    External     | ?cpp_func@@YAHH@Z (int __cdecl cpp_func(int))
089 00000000 SECT22 notype ()    External     | _c_func
08A 00000000 SECT24 notype ()    External     | _main
...
```

W takim przypadku określ nazwy jako `?cpp_func@@YAHH@Z`, `c_func`, i `main` w pliku odpowiedzi.

Jeśli istnieje więcej niż jedna **/kolejność** opcja jest wyświetlana w obszarze Opcje konsolidatora, obowiązuje ostatnią określony.

**/Kolejność** opcja powoduje wyłączenie konsolidowania przyrostowego. Mogą pojawić się ostrzeżenie konsolidatora [LNK4075](../../error-messages/tool-errors/linker-tools-warning-lnk4075.md) po określeniu tę opcję, jeśli konsolidowania przyrostowego jest włączona lub jeśli określono [/zi (przyrostowe PDB)](../../build/reference/z7-zi-zi-debug-information-format.md) — opcja kompilatora. O wyłączeniu tego ostrzeżenia, należy użyć [/incremental: No](../../build/reference/incremental-link-incrementally.md) — opcja konsolidatora wyłączyć konsolidowania przyrostowego i używanie [/zi (Generuj plik PDB)](../../build/reference/z7-zi-zi-debug-information-format.md) opcję kompilatora, aby wygenerować pliku PDB bez konsolidacji przyrostowej.

> [!NOTE]
> ŁĄCZE nie można uporządkować statyczne funkcje, ponieważ nazwy funkcji statyczne nie są nazw symboli publicznych. Gdy **/kolejność** jest określona, konsolidator ostrzeżenie [LNK4037](../../error-messages/tool-errors/linker-tools-warning-lnk4037.md) jest generowany dla każdego symbolu w pliku odpowiedzi zlecenia, który jest statyczny lub nie została znaleziona.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio

1. Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Ustawianie właściwości projektu Visual C++](../../ide/working-with-project-properties.md).  

1. W obszarze **właściwości konfiguracji**, otwórz **konsolidatora** , a następnie wybierz **optymalizacji** strony właściwości.

1. Modyfikowanie **kolejność funkcji** właściwość zawiera nazwę pliku odpowiedzi.

### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.FunctionOrder%2A>.

## <a name="see-also"></a>Zobacz też

[Ustawianie opcji konsolidatora](../../build/reference/setting-linker-options.md)  
[Opcje konsolidatora](../../build/reference/linker-options.md)