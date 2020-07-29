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
ms.openlocfilehash: 114ed4a279b66571c0dc81fc1139dcdc59c17eae
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87234318"
---
# <a name="zcwchar_t-wchar_t-is-native-type"></a>/Zc:wchar_t (wchar_t jest typem natywnym)

Przeanalizuj **`wchar_t`** jako typ wbudowany zgodnie ze standardem C++.

## <a name="syntax"></a>Składnia

> **/Zc: wchar_t**[ **-** ]

## <a name="remarks"></a>Uwagi

Jeśli **/Zc: wchar_t** jest włączona, **`wchar_t`** jest słowem kluczowym dla wbudowanego typu całkowitego w kodzie skompilowanym jako C++. Jeśli określono **/Zc: wchar_t-** (ze znakiem minus) lub kod skompilowany jako C, **`wchar_t`** nie jest typem wbudowanym. Zamiast tego **`wchar_t`** jest zdefiniowany jako **`typedef`** dla **`unsigned short`** w nagłówku kanonicznym STDDEF. h. (Implementacja firmy Microsoft definiuje ją w innym nagłówku, który jest zawarty w STDDEF. h i innych standardowych nagłówkach).

Nie zalecamy **/Zc: wchar_t —** ponieważ standard C++ wymaga, aby **`wchar_t`** był typem wbudowanym. Korzystanie z **`typedef`** wersji może spowodować problemy z przenośnością. W przypadku uaktualniania z wcześniejszych wersji programu Visual Studio i napotkania błędu kompilatora [C2664](../../error-messages/compiler-errors-2/compiler-error-c2664.md) , ponieważ kod próbuje niejawnie skonwertować **`wchar_t`** do **`unsigned short`** , zalecamy zmianę kodu, aby naprawić błąd, zamiast ustawiania **/Zc: wchar_t-**.

Opcja **/Zc: wchar_t** jest domyślnie włączona w kompilacjach języka C++ i jest ignorowana w kompilacjach C. Opcja [/permissive-](permissive-standards-conformance.md) nie ma wpływu na **/Zc: wchar_t**.

Firma Microsoft implementuje **`wchar_t`** jako dwubajtową wartość bez znaku. Jest on mapowany na typ natywny specyficzny dla firmy Microsoft **`__wchar_t`** . Aby uzyskać więcej informacji na temat **`wchar_t`** , zobacz [zakresy typów danych](../../cpp/data-type-ranges.md) i [typy podstawowe](../../cpp/fundamental-types-cpp.md).

Jeśli piszesz nowy kod, który ma współpracować ze starszym kodem, który nadal używa **`typedef`** wersji programu **`wchar_t`** , możesz zapewnić przeciążenia zarówno dla programu **`unsigned short`** , jak i dla każdej **`__wchar_t`** z **`wchar_t`** nich, aby kod można było połączyć z kodem skompilowanym z **/Zc: wchar_t** lub kodu skompilowanego bez tego. W przeciwnym razie trzeba będzie udostępnić dwa różne kompilacje biblioteki, jeden z i jeden bez **/Zc: wchar_t** włączone. Nawet w tym przypadku zaleca się kompilowanie starszego kodu za pomocą tego samego kompilatora, którego używa się do kompilowania nowego kodu. Nigdy nie mieszaj plików binarnych skompilowanych różnymi kompilatorami.

Gdy **/Zc: wchar_t** jest określony, definiowane są ** \_ WCHAR \_ t \_ zdefiniowane** i ** \_ natywne \_ \_ \_ zdefiniowane symbole WCHAR t** . Aby uzyskać więcej informacji, zobacz [wstępnie zdefiniowane makra](../../preprocessor/predefined-macros.md).

Jeśli w kodzie są używane funkcje globalne kompilatora COM, ponieważ **/Zc: wchar_t** jest teraz domyślnie włączone, zalecamy zmianę jawnych odwołań do comsupp. lib (z [komentarza pragma](../../preprocessor/comment-c-cpp.md) lub w wierszu polecenia) na comsuppw. lib lub comsuppwd. lib. (Jeśli musisz skompilować przy użyciu **/Zc: wchar_t-**, użyj comsupp. lib). Jeśli dołączysz plik nagłówka comdef. h, poprawna biblioteka zostanie określona dla Ciebie. Informacje o obsłudze kompilatora COM można znaleźć w temacie [Obsługa kompilatora com](../../cpp/compiler-com-support.md).

**`wchar_t`** Typ wbudowany nie jest obsługiwany podczas kompilowania kodu C. Aby uzyskać więcej informacji na temat problemów ze zgodnością Visual C++, zobacz [niestandardowe zachowanie](../../cpp/nonstandard-behavior.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz okno dialogowe **strony właściwości** projektu. Aby uzyskać szczegółowe informacje, zobacz [Ustawianie kompilatora C++ i właściwości kompilacji w programie Visual Studio](../working-with-project-properties.md).

1. Wybierz **Configuration Properties**  >  stronę języka**C/C++** właściwości konfiguracji  >  **Language** .

1. Zmodyfikuj **Wchar_t Traktuj jako właściwość typu wbudowanego** .

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz: <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.TreatWChar_tAsBuiltInType%2A>.

## <a name="see-also"></a>Zobacz także

[/Zc (Zgodność)](zc-conformance.md)<br/>
