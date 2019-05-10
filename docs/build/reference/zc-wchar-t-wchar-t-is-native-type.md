---
title: /Zc:wchar_t (wchar_t jest typem natywnym)
ms.date: 03/01/2018
f1_keywords:
- VC.Project.VCCLWCECompilerTool.TreatWChar_tAsBuiltInType
- VC.Project.VCCLCompilerTool.TreatWChar_tAsBuiltInType
- /Zc:wchar_t
helpviewer_keywords:
- /Zc compiler options [C++]
- -Zc compiler options [C++]
- wchar_t type
- Conformance compiler options
- Zc compiler options [C++]
ms.assetid: b0de5a84-da72-4e5a-9a4e-541099f939e0
ms.openlocfilehash: 962bb2aaa2f05ad0dc4c9c86cd5cc9694cfad98b
ms.sourcegitcommit: 7d64c5f226f925642a25e07498567df8bebb00d4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2019
ms.locfileid: "65446160"
---
# <a name="zcwchart-wchart-is-native-type"></a>/Zc:wchar_t (wchar_t jest typem natywnym)

Analizowanie `wchar_t` jako typu wbudowanego zgodnie ze standardem C++.

## <a name="syntax"></a>Składnia

> **/ Zc:**[**-**]

## <a name="remarks"></a>Uwagi

Jeśli **/Zc:** jest włączona, `wchar_t` jest słowem kluczowym dla typu całkowitego wbudowanego w kodzie skompilowanym jako C++. Jeśli **/Zc:wchar_t-** (ze znakiem minus) jest określony, lub w kodzie skompilowany jako C, `wchar_t` nie jest typem wbudowanym. Zamiast tego `wchar_t` jest zdefiniowany jako `typedef` dla `unsigned short` w stddef.h canonical nagłówka. (Implementacja firmy Microsoft definiuje go w innym nagłówkiem, który znajduje się w stddef.h i innych standardowych nagłówków.)

Nie zaleca się **/Zc:wchar_t-** ponieważ C++ standardowa wymaga, aby `wchar_t` był typem wbudowanym. Za pomocą `typedef` wersji może spowodować problemy z przenośnością. Jeśli uaktualnienia ze starszych wersji programu Visual Studio i występuje błąd kompilatora [C2664](../../error-messages/compiler-errors-2/compiler-error-c2664.md) ponieważ kod próbuje niejawnie skonwertować `wchar_t` do `unsigned short`, zaleca się zmiany kodu, aby naprawić błąd, Zamiast ustawiać **/Zc:wchar_t-**.

**/Zc:** opcja jest włączona domyślnie w C++ kompilacje i w kompilacjach kodu języka C jest ignorowana. [/ Permissive-](permissive-standards-conformance.md) opcji nie ma wpływu na **/Zc:**.

Firma Microsoft implementuje `wchar_t` jako wartości bez znaku dwubajtowego. Jest on mapowany do typu macierzystego specyficzne dla firmy Microsoft `__wchar_t`. Aby uzyskać więcej informacji na temat `wchar_t`, zobacz [zakresy typu danych](../../cpp/data-type-ranges.md) i [podstawowych typów](../../cpp/fundamental-types-cpp.md).

Jeśli piszesz nowy kod, który ma pod kątem współdziałania z starszego kodu, który nadal używa `typedef` wersję `wchar_t`, możesz podać przeciążenia zarówno `unsigned short` i `__wchar_t` wariantów `wchar_t`, dzięki czemu kod może być połączona z kod skompilowany przy użyciu **/Zc:** lub kod skompilowany bez niego. W przeciwnym razie trzeba zapewnić dwie kompilacje biblioteki: jeden z, a drugi bez **/Zc:** włączone. Nawet w tym przypadku zaleca się kompilowanie starszego kodu za pomocą tego samego kompilatora, którego używa się do kompilowania nowego kodu. Nigdy nie mieszaj plików binarnych skompilowanych różnymi kompilatorami.

Gdy **/Zc:** jest określony,  **\_WCHAR\_T\_zdefiniowane** i  **\_NATYWNYCH\_WCHAR\_T\_zdefiniowane** symbole są zdefiniowane. Aby uzyskać więcej informacji, zobacz [wstępnie zdefiniowane makra](../../preprocessor/predefined-macros.md).

Jeśli kod używa funkcje globalne kompilatora COM, ponieważ **/Zc:** jest teraz na domyślnie, zaleca się zmianę jawnych odwołań do comsupp.lib (z [komentarz pragma](../../preprocessor/comment-c-cpp.md) lub na wiersza polecenia) na comsuppw.lib lub comsuppwd.lib. (Jeśli musisz skompilować z **/Zc:wchar_t-**, użyj comsupp.lib.) Jeśli dołączasz plik nagłówkowy comdef.h, odpowiednia biblioteka jest określana automatycznie. Aby uzyskać informacje na temat obsługi kompilatora COM, zobacz [Compiler COM Support](../../cpp/compiler-com-support.md).

`wchar_t` Wbudowany typ nie jest obsługiwane, podczas kompilowania kodu c. Aby uzyskać więcej informacji na temat problemów ze zgodnością w języku Visual C++, zobacz [niestandardowe zachowanie](../../cpp/nonstandard-behavior.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [kompilatora i tworzenia właściwości ustaw C++ w programie Visual Studio](../working-with-project-properties.md).

1. Wybierz **właściwości konfiguracji** > **C/C++** > **języka** strony.

1. Modyfikowanie **Traktuj wchar_t jako typ wbudowany** właściwości.

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.TreatWChar_tAsBuiltInType%2A>.

## <a name="see-also"></a>Zobacz także

[/Zc (Zgodność)](zc-conformance.md)<br/>
