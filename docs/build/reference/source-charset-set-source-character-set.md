---
title: / Source-Charset (Ustaw źródłowy zestaw znaków)
ms.date: 02/06/2019
f1_keywords:
- source-charset
- /source-charset
helpviewer_keywords:
- /execution-charset compiler option
ms.assetid: d3c5bf7f-526d-4ee4-acc5-c1a02a4fc481
ms.openlocfilehash: 2a204000be6e4e434b6ef4aabf6bbc0db1593fb0
ms.sourcegitcommit: bd637e9c39650cfd530520ea978a22fa4caa0e42
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/07/2019
ms.locfileid: "55849720"
---
# <a name="source-charset-set-source-character-set"></a>/ Source-Charset (Ustaw źródłowy zestaw znaków)

Umożliwia określenie znaków źródła, ustaw dla Twojego pliku wykonywalnego.

## <a name="syntax"></a>Składnia

```
/source-charset:[IANA_name|.CPID]
```

## <a name="arguments"></a>Argumenty

**IANA_name**<br/>
Nazwa zestawu znaków zdefiniowanych przez organizację IANA.

**CPID**<br/>
Identyfikator strony kodu jako liczba dziesiętna.

## <a name="remarks"></a>Uwagi

Możesz użyć **/Source-Charset** opcję, aby określić zestaw znaków rozszerzonych źródło do użycia podczas swoje pliki źródłowe zawierają znaki, które nie są reprezentowane w zestawie znaków podstawowego źródła. Źródłowy zestaw znaków jest poprawnie zakodowany używaną do interpretacji parametru tekst źródłowy programu do wewnętrznej reprezentacji używany jako dane wejściowe fazy przetwarzania wstępnego przed kompilacją. Wewnętrznej reprezentacji jest następnie konwertowana na zestaw znaków wykonania do przechowywania ciągów i wartości w pliku wykonywalnym. Możesz użyć albo organizację IANA nazwy zestawu znaków ISO lub pojedynczego znaku kropki (.), a następnie przez identyfikator 3 – 5 cyfr kodu dziesiętnego strony, aby określić używany zestaw znaków. Aby uzyskać listę obsługiwanych identyfikatorami stronę kodu i nazwy zestawu znaków, zobacz [kodu strony identyfikatory](/windows/desktop/Intl/code-page-identifiers).

Domyślnie program Visual Studio wykrywa znacznika kolejności bajtów, aby określić, czy plik źródłowy jest w formacie zakodowanym Unicode, na przykład, UTF-16 lub UTF-8. Jeśli zostanie znaleziony Brak znacznika kolejności bajtów, zakłada się pliku źródłowego jest zakodowane przy użyciu bieżącej stronie kodowej użytkownika, chyba że określono nazwę lub kod strony zbiór znaków za pomocą **/Source-Charset** opcji. Program Visual Studio umożliwia zapisywanie kodu źródłowego języka C++ za pomocą jednej z kilku kodowania znaków. Aby uzyskać więcej informacji na temat zestawów znaków źródła i wykonania, zobacz [zestawy znaków](../../cpp/character-sets.md) w dokumentacji języka.

Źródłowy zestaw znaków, które podasz znaki ASCII 7-bitowego musi być mapowane do tego samego punkty kodowe w zestawie znaków lub mogą wykonać wiele błędów kompilacji. Zestaw znaków źródła musi być możliwe do zamapowania na rozszerzonego zestawu znaków Unicode, można kodować, UTF-8. Znaki, które nie są można kodować w formacie UTF-8 są reprezentowane przez zastępuje specyficzne dla implementacji. Kompilator Microsoft używa znaku zapytania tych znaków.

Jeśli chcesz ustawić zestaw znaków źródła i wykonania zestawu znaków na UTF-8, możesz użyć **/UTF-8** — opcja kompilatora jako skrót. Jest równoznaczne z użyciem **/source-charset:utf-8 /execution-charset:utf-8** w wierszu polecenia. Żadnego z tych opcji również włącza **/Validate-Charset** opcja domyślnie.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).

1. Rozwiń **właściwości konfiguracji**, **C/C++**, **wiersza polecenia** folderu.

1. W **dodatkowe opcje**, Dodaj **/Source-Charset** opcji, a następnie określ preferowany kodowania.

1. Wybierz **OK** Aby zapisać zmiany.

## <a name="see-also"></a>Zobacz też

[Opcje kompilatora](../../build/reference/compiler-options.md)<br/>
[Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)<br/>
[/ Execution-Charset (Ustaw zestaw znaków wykonywania)](../../build/reference/execution-charset-set-execution-character-set.md)<br/>
[/utf-8 (Ustaw źródłowy i wykonywalny zestaw znaków na UTF-8)](../../build/reference/utf-8-set-source-and-executable-character-sets-to-utf-8.md)<br/>
[/validate-charset (Zweryfikuj zgodność znaków)](../../build/reference/validate-charset-validate-for-compatible-characters.md)