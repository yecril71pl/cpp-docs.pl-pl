---
title: /ZW (Kompilacja środowiska wykonawczego systemu Windows)
ms.date: 04/08/2019
f1_keywords:
- VC.Project.VCCLCompilerTool.CompileAsWinRT
- /zw
helpviewer_keywords:
- /ZW
- -ZW compiler option
- /ZW compiler option
- -ZW
- Windows Runtime compiler option
ms.assetid: 0fe362b0-9526-498b-96e0-00d7a965a248
ms.openlocfilehash: 0808f66c4d4c4e99b3038ea18a1f71f4ebaca89a
ms.sourcegitcommit: 7d64c5f226f925642a25e07498567df8bebb00d4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2019
ms.locfileid: "65446176"
---
# <a name="zw-windows-runtime-compilation"></a>/ZW (Kompilacja środowiska wykonawczego systemu Windows)

Kompiluje źródła kod obsługujący Microsoft C++ rozszerzenia składnika C++/CX do tworzenia aplikacji uniwersalnych platformy Windows (UWP).

Kiedy używasz **/ZW** skompilować, należy zawsze określić **/ehsc** także.

## <a name="syntax"></a>Składnia

```cpp
/ZW /EHsc
/ZW:nostdlib /EHsc
```

## <a name="arguments"></a>Argumenty

**nostdlib**<br/>
Wskazuje, że Platform.winmd Windows.Foundation.winmd i inne domyślne, które pliki metadanych (.winmd) Windows nie są automatycznie uwzględniane w kompilacji. Zamiast tego należy użyć [/FU (nazwij wymuszone #using)](fu-name-forced-hash-using-file.md) — opcja kompilatora jawnie określić pliki metadanych Windows.

## <a name="remarks"></a>Uwagi

Po określeniu **/ZW** opcja, kompilator obsługuje te funkcje:

- Pliki wymagane metadane, przestrzenie nazw, typów danych i funkcje wymagane przez aplikację do środowiska wykonawczego Windows.

- Automatyczne zliczanie odwołań obiektów Windows Runtime i automatyczne odrzucanie obiektu podczas jego licznik odwołań zbliża się do zera.

Ponieważ konsolidatora przyrostowego nie obsługuje metadanych Windows dołączona do plików .obj przy użyciu **/ZW** opcję przestarzałego [/Gm (Włącz minimalną ponowną kompilację)](gm-enable-minimal-rebuild.md) opcja jest niezgodna z **/ZW**.

Aby uzyskać więcej informacji, zobacz [odwołanie językowe Visual C++](../../cppcx/visual-c-language-reference-c-cx.md).

## <a name="requirements"></a>Wymagania

## <a name="see-also"></a>Zobacz także

[Opcje kompilatora MSVC](compiler-options.md)<br/>
[Składnia wiersza polecenia kompilatora MSVC](compiler-command-line-syntax.md)
