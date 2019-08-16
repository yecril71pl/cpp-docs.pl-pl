---
title: określono element/source-charset (Ustaw źródłowy zestaw znaków)
ms.date: 02/06/2019
f1_keywords:
- source-charset
- /source-charset
helpviewer_keywords:
- /execution-charset compiler option
ms.assetid: d3c5bf7f-526d-4ee4-acc5-c1a02a4fc481
ms.openlocfilehash: cd3e4eb3fd305ba6bdd298d18b1edb80f2b98343
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69498257"
---
# <a name="source-charset-set-source-character-set"></a>określono element/source-charset (Ustaw źródłowy zestaw znaków)

Umożliwia określenie zestawu znaków źródłowych dla pliku wykonywalnego.

## <a name="syntax"></a>Składnia

```
/source-charset:[IANA_name|.CPID]
```

## <a name="arguments"></a>Argumenty

**IANA_name**<br/>
Nazwa zestawu znaków zdefiniowanego przez organizację IANA.

**CPID**<br/>
Identyfikator strony kodowej jako liczbę dziesiętną.

## <a name="remarks"></a>Uwagi

Można użyć opcji **określono element/source-charset** , aby określić rozszerzony zestaw znaków źródła, który ma być używany, gdy pliki źródłowe zawierają znaki, które nie są reprezentowane w podstawowym zestawie znaków źródła. Zestaw znaków źródła jest kodowaniem używanym do interpretowania tekstu źródłowego programu w wewnętrznej reprezentacji używanej jako dane wejściowe do faz przetwarzania wstępnego przed kompilacją. Reprezentacja wewnętrzna jest następnie konwertowana na zestaw znaków wykonywania w celu przechowywania wartości ciągów i znaków w pliku wykonywalnym. Aby określić zestaw znaków, który ma być używany, można użyć nazwy zestawu znaków IANA lub ISO albo kropki (.), a następnie cyfry od 3 do 5 cyfr dziesiętnego identyfikatora strony kodowej. Aby uzyskać listę obsługiwanych identyfikatorów stron kodowych i nazw zestawów znaków, zobacz [identyfikatory stron kodowych](/windows/win32/Intl/code-page-identifiers).

Domyślnie program Visual Studio wykrywa znacznik kolejności bajtów, aby określić, czy plik źródłowy jest w zakodowanym formacie Unicode, na przykład UTF-16 lub UTF-8. Jeśli nie zostanie znaleziony znacznik kolejności bajtów, zakłada, że plik źródłowy jest zakodowany przy użyciu bieżącej strony kodowej użytkownika, o ile nie zostanie określona nazwa zestawu znaków ani strona kodowa przy użyciu opcji **określono element/source-charset** . Program Visual Studio umożliwia zapisanie kodu C++ źródłowego przy użyciu dowolnego z kilku kodowań znaków. Aby uzyskać więcej informacji na temat zestawów znaków źródła i wykonania, zobacz [zestawy znaków](../../cpp/character-sets.md) w dokumentacji języka.

Określony źródłowy zestaw znaków musi mapować 7-bitowe znaki ASCII na te same punkty kodu w zestawie znaków lub wiele błędów kompilacji, które mogą wystąpić. Zestaw znaków źródłowych musi być również Mappable do rozszerzonego zestawu znaków Unicode encodable przez UTF-8. Znaki, które nie są encodable w UTF-8 są reprezentowane przez podstawienie specyficzne dla implementacji. Kompilator firmy Microsoft używa znaku zapytania dla tych znaków.

Jeśli chcesz ustawić zestaw znaków źródła i zestaw znaków wykonania na UTF-8, możesz użyć opcji kompilatora **/UTF-8** jako skrótu. Jest równoważne określeniu **określono element/source-charset: UTF-8/Execution-charset: UTF-8** w wierszu polecenia. Każda z tych opcji domyślnie włącza opcję **/Validate-charset** .

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz okno dialogowe **strony właściwości** projektu. Aby uzyskać więcej informacji, [Zobacz C++ Ustawianie właściwości kompilatora i Build w programie Visual Studio](../working-with-project-properties.md).

1. Rozwiń węzeł **Właściwości konfiguracji**, **C/C++** , **wiersz polecenia** .

1. W obszarze **Opcje dodatkowe**Dodaj opcję **określono element/source-charset** i określ preferowane kodowanie.

1. Wybierz **przycisk OK** , aby zapisać zmiany.

## <a name="see-also"></a>Zobacz także

[Opcje kompilatora MSVC](compiler-options.md)<br/>
[Składnia wiersza polecenia kompilatora MSVC](compiler-command-line-syntax.md)<br/>
[/Execution-charset (Ustaw zestaw znaków wykonywania)](execution-charset-set-execution-character-set.md)<br/>
[/utf-8 (Ustaw źródłowy i wykonywalny zestaw znaków na UTF-8)](utf-8-set-source-and-executable-character-sets-to-utf-8.md)<br/>
[/validate-charset (Zweryfikuj zgodność znaków)](validate-charset-validate-for-compatible-characters.md)
