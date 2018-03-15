---
title: '/ Zc: wchar_t (wchar_t jest typem natywnym) | Dokumentacja firmy Microsoft'
ms.custom: 
ms.date: 03/01/2018
ms.technology:
- cpp-tools
ms.topic: article
f1_keywords:
- VC.Project.VCCLWCECompilerTool.TreatWChar_tAsBuiltInType
- VC.Project.VCCLCompilerTool.TreatWChar_tAsBuiltInType
- /Zc:wchar_t
dev_langs:
- C++
helpviewer_keywords:
- /Zc compiler options [C++]
- -Zc compiler options [C++]
- wchar_t type
- Conformance compiler options
- Zc compiler options [C++]
ms.assetid: b0de5a84-da72-4e5a-9a4e-541099f939e0
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: d4970e4aba8bf2d6aebf60f876a4770b18943781
ms.sourcegitcommit: eeb2b5ad8d3d22514a7b9bd7d756511b69ae0ccf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2018
---
# <a name="zcwchart-wchart-is-native-type"></a>/Zc:wchar_t (wchar_t jest typem natywnym)

Przeanalizować `wchar_t` jako typ wbudowany zgodnie z C++ standard.

## <a name="syntax"></a>Składnia

> **/ Zc:**[**-**]

## <a name="remarks"></a>Uwagi

Jeśli **/Zc:** jest włączona, `wchar_t` jest słowem kluczowym dla typu całkowitego wbudowanych w kodzie skompilowanym jako C++. Jeśli **/Zc:wchar_t-** (ze znakiem minus) jest określona, lub w kodzie skompilowany jako C, `wchar_t` nie jest typem wbudowanym. Zamiast tego `wchar_t` jest zdefiniowany jako `typedef` dla `unsigned short` w stddef.h canonical nagłówka. (Przez firmę Microsoft implementacją definiuje go w innym nagłówkiem, który jest dołączony przez stddef.h i innych standardowych nagłówków.)

Nie zaleca się **/Zc:wchar_t-** ponieważ C++ standard wymaga, aby `wchar_t` być typem wbudowanym. Przy użyciu `typedef` wersji może spowodować problemy z przenośnością. Jeśli uaktualnienie z wcześniejszych wersji programu Visual C++ i wystąpi błąd kompilatora [C2664](../../error-messages/compiler-errors-2/compiler-error-c2664.md) ponieważ kod jest w trakcie niejawnie przekonwertować `wchar_t` do `unsigned short`, firma Microsoft zaleca, aby zmienić kod, aby naprawić błąd, zamiast tego ustawienia **/Zc:wchar_t-**.

**/Zc:** opcja jest włączona domyślnie w kompilacjach kodu C++ i jest ignorowany w kompilacjach kodu C. [/ Ograniczająca-](permissive-standards-conformance.md) opcji nie ma wpływu na **/Zc:**.

Implementuje Microsoft `wchar_t` jako wartość bez znaku dwubajtowego. Mapowania typu macierzystego specyficzne dla firmy Microsoft `__wchar_t`. Aby uzyskać więcej informacji na temat `wchar_t`, zobacz [zakresy typu danych](../../cpp/data-type-ranges.md) i [podstawowych typów](../../cpp/fundamental-types-cpp.md).

Podczas pisania nowy kod, który ma na potrzeby współdziałania z starszego kodu, który nadal używa `typedef` wersji `wchar_t`, możesz podać przeciążenia dla obu `unsigned short` i `__wchar_t` zmian `wchar_t`, dzięki czemu kod może być połączony z kodu skompilowanego z **/Zc:** lub kodu skompilowanego bez niego. W przeciwnym razie trzeba podać dwóch różnych kompilacji biblioteki: jeden z, a drugi bez **/Zc:** włączone. Nawet w tym przypadku zaleca się kompilowanie starszego kodu za pomocą tego samego kompilatora, którego używa się do kompilowania nowego kodu. Nigdy nie mieszaj plików binarnych skompilowanych różnymi kompilatorami.

Gdy **/Zc:** jest określony,  **\_WCHAR\_T\_zdefiniowane** i  **\_NATYWNEGO\_WCHAR\_T\_zdefiniowane** zdefiniowanych symboli. Aby uzyskać więcej informacji, zobacz [wstępnie zdefiniowane makra](../../preprocessor/predefined-macros.md).

Jeśli kod wykorzystuje funkcje globalne kompilatora COM, ponieważ **/Zc:** jest teraz na domyślnie, zaleca się zmianę jawnego odwołania do comsupp.lib (albo z [komentarz pragma](../../preprocessor/comment-c-cpp.md) lub na wiersza polecenia) comsuppw.lib lub comsuppwd.lib. (Jeśli należy skompilować z **/Zc:wchar_t-**, użyj comsupp.lib.) Jeśli dołączasz plik nagłówkowy comdef.h, odpowiednia biblioteka jest określana automatycznie. Informacje na temat kompilatora COM obsługi, zobacz [obsługi modelu COM kompilatora](../../cpp/compiler-com-support.md).

`wchar_t` Typ wbudowany nie jest obsługiwane podczas kompilowania kodu C. Aby uzyskać więcej informacji na temat problemów zgodności z programem Visual C++, zobacz [niestandardowe zachowanie](../../cpp/nonstandard-behavior.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).

1. Wybierz **właściwości konfiguracji** > **C/C++** > **języka** strony.

1. Modyfikowanie **Traktuj wchar_t jako typ wbudowany** właściwości.

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.TreatWChar_tAsBuiltInType%2A>.

## <a name="see-also"></a>Zobacz także

[/Zc (Zgodność)](../../build/reference/zc-conformance.md)<br/>
