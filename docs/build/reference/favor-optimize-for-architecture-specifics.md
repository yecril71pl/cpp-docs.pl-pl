---
title: /favor (optymalizacja pod kątem specyfiki architektury)
ms.date: 11/04/2016
f1_keywords:
- /favor
helpviewer_keywords:
- -favor compiler option [C++]
- /favor compiler option [C++]
ms.assetid: ad264df2-e30f-4d68-8bd0-10d6bee71a2a
ms.openlocfilehash: 63affcced5dfc5bb56b0226021e1c32d93ec5d4f
ms.sourcegitcommit: ff3cbe4235b6c316edcc7677f79f70c3e784ad76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/19/2018
ms.locfileid: "53626750"
---
# <a name="favor-optimize-for-architecture-specifics"></a>/favor (optymalizacja pod kątem specyfiki architektury)

**/ favor:** `option` generuje kod, który jest zoptymalizowany dla określonej architektury lub kątem specyfiki architektury micro AMD i architektur Intel.

## <a name="syntax"></a>Składnia

> **/ favor:**{**blend** | **ATOM** | **AMD64** | **INTEL64**}

## <a name="remarks"></a>Uwagi

**/favor:Blend**<br/>
(x86 i x64) tworzy kod, który jest zoptymalizowany pod kątem specyfiki architektury micro AMD i architektur Intel. Gdy **/favor:blend** może nie być najlepszą wydajność możliwe na konkretny procesor, kwotę ustalono, aby zapewnić najlepszą wydajność do szerokiego zakresu x86 i x64 procesorów. Domyślnie **/favor:blend** jest aktywna.

**/favor:Atom**<br/>
(x86 i x64) tworzy kod, który jest zoptymalizowany pod kątem specyfiki procesora Intel Atom i technologii firmy Intel Centrino Atom procesora. Kod, który jest generowany przy użyciu **/favor:ATOM** może utworzyć również instrukcje instrukcji SSSE3 firmy Intel, instrukcji SSE3, SSE2 i SSE dla procesorów Intel.

**/favor:AMD64**<br/>
— tylko x64 64 optymalizuje wygenerowanego kodu AMD Opteron i procesorów Athlon, które obsługują rozszerzenia 64-bitowe. Zoptymalizowany kod może działać na wszystkich x64 zgodne platformy. Kod, który jest generowany przy użyciu **/favor:AMD64** może spowodować zmniejszenie wydajności na procesorach Intel, które obsługują Intel64.

**/favor:INTEL64**<br/>
— tylko x64 64 optymalizuje kod generowany dla procesorów Intel, które obsługują Intel64, która zwykle daje w wyniku lepszą wydajność dla danej platformy. Wynikowy kod może działać na dowolnym x64 platformy. Kod, który jest generowany przy użyciu **/favor:INTEL64** może spowodować zmniejszenie wydajności na AMD Opteron oraz procesory Athlon, obsługujące rozszerzenia 64-bitowych.

> [!NOTE]
> Architektura Intel64 była wcześniej znana jako technologia Extended Memory 64, a odpowiadające opcje kompilatora był **/favor:EM64T**.

Aby uzyskać informacje na temat programu x64 architektury, zobacz [x64 konwencje kodowania](../../build/x64-software-conventions.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).

1. Wybierz **C/C++** folderu.

1. Wybierz **wiersza polecenia** stronę właściwości.

1. Wpisz opcję kompilatora w **dodatkowe opcje** pole.

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Zobacz też

[Opcje kompilatora](../../build/reference/compiler-options.md)<br/>
[Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)