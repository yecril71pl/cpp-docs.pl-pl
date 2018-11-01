---
title: Zestawy znaków
ms.date: 04/12/2018
helpviewer_keywords:
- Character sets
- basic source character set (C++)
- universal character names
- basic execution character set (C++)
ms.assetid: 379a2af6-6422-425f-8352-ef0bca6c0d74
ms.openlocfilehash: 5282d5b227e71c0ba6f822a9534a8a31cbd86db9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50664636"
---
# <a name="character-sets"></a>Zestawy znaków

Tekst program w języku C++ są przechowywane w plikach źródłowych, korzystających z kodowaniem określonego znaku. C++ standard określa zestawu znaków podstawowgoe źródła dla plików źródłowych i podstawowym zestawie egzekucji znaków dla skompilowanych plików. Visual C++ umożliwia dodatkowego zestawu znaków specyficznych dla ustawień regionalnych, które ma być używany w plikach źródłowych i skompilowane pliki.

## <a name="character-sets"></a>Zestawy znaków

Określa C++ standard *zestaw znaków podstawowego źródła* , mogą być używane w plikach źródłowych. Do reprezentowania znaków spoza tego zestawu, można określić dodatkowe znaki przy użyciu *znaki uniwersalne nazwy*. Po skompilowaniu *zestaw znaków wykonania podstawowego* i *zestaw znaków dwubajtowych wykonania podstawowego* reprezentują znaków i ciągów, które mogą być wyświetlane w programie. Implementacja języka Visual C++ umożliwia dodatkowe znaki w kodzie źródłowym i skompilowanego kodu.

### <a name="basic-source-character-set"></a>Zestaw znaków podstawowego źródła

*Zestaw znaków podstawowego źródła* składa się z 96 znaków, które mogą być używane w plikach źródłowych. Ten zestaw zawiera znak spacji, tabulator poziomy, tabulator pionowy, wciągnięcia kartki i znaki nowego wiersza, a to zestaw znaków graficznych:

`a b c d e f g h i j k l m n o p q r s t u v w x y z`

`A B C D E F G H I J K L M N O P Q R S T U V W X Y Z`

`0 1 2 3 4 5 6 7 8 9`

`_ { } [ ] # ( ) < > % : ; . ? * + - / ^ & | ~ ! = , \ " '`

**Microsoft Specific**

Visual C++ dołącza `$` znaków będący członkiem zestaw znaków podstawowego źródła. Visual C++ pozwala uzyskać dodatkowy zestaw znaków do użycia w plikach źródłowych, w oparciu o kodowanie pliku. Domyślnie program Visual Studio są przechowywane pliki źródłowe przy użyciu domyślną stroną kodową. Gdy pliki źródłowe są zapisywane przy użyciu strony kodowej specyficzne dla ustawień regionalnych lub na stronę kodową Unicode, Visual C++ pozwala na używanie znaków tę stronę kodową w kodzie źródłowym z wyjątkiem kody sterujące, nie są jawnie dozwolone w znaków podstawowgoe źródła ustawiona. Na przykład można umieścić znaki japońskie komentarze, identyfikatory lub literałów ciągów, jeśli zapiszesz plik przy użyciu japoński stronę kodową. Visual C++ nie zezwala na sekwencje znaków, które nie można przetłumaczyć prawidłowych znaków wielobajtowych lub punkty kodowe Unicode. W zależności od opcji kompilatora nie wszystkie dozwolonych znaków mogą występować w identyfikatorów. Aby uzyskać więcej informacji, zobacz [identyfikatory](../cpp/identifiers-cpp.md).

**END specyficzny dla Microsoft**

### <a name="universal-character-names"></a>Uniwersalne nazwy znaków

Ponieważ programy C++ mogą używać wielu więcej znaków niż określone w zestawie znaków podstawowego źródła, należy określić te znaki w taki sposób, przenośne za pomocą *uniwersalne nazwy znaków*. Nazwa znaki uniwersalne składa się z sekwencji znaków, które reprezentują punkt kodu Unicode.  Wykonaj te dwie formy. Użyj `\UNNNNNNNN` reprezentuje punkt kodu Unicode w postaci U + NNNNNNNN, gdzie NNNNNNNN to numer punktu osiem cyfr kodu szesnastkowego. Użycie czterech cyfr `\uNNNN` reprezentuje punkt kodu Unicode w postaci U + 0000NNNN.

Uniwersalne nazwy znaków może służyć w identyfikatorach, a w literałach ciągów i znakowe. Nazwa znaki uniwersalne nie może służyć do reprezentowania punkt kodu zastępczy z zakresu od 0xD800-0xDFFF. Zamiast tego należy użyć punktu odpowiedni kod; kompilator automatycznie generuje wszelkie wymagane surogaty. Dodatkowe ograniczenia dotyczą uniwersalne nazwy znaków, które mogą być używane w identyfikatorach. Aby uzyskać więcej informacji, zobacz [identyfikatory](../cpp/identifiers-cpp.md) i [literały ciągów i znakowe](../cpp/string-and-character-literals-cpp.md).

**Microsoft Specific**

Kompilator języka Visual C++ traktuje znak w charakterze uniwersalnym nazwa literału w formularzach i zamiennie. Na przykład można zadeklarować identyfikatora przy użyciu formy nazwy znaki uniwersalne i używać go w postaci literału:

```cpp
auto \u30AD = 42; // \u30AD is 'キ'
if (キ == 42) return true; // \u30AD and キ are the same to the compiler
```

Format znaków rozszerzonych w Schowku Windows jest specyficzne dla ustawień regionalnych aplikacji. Wycinanie i wklejanie tych znaków w kodzie z innej aplikacji może spowodować nieoczekiwany znak kodowania. Może to spowodować błędów analizy przy użyciu bez widocznej przyczyny w kodzie. Firma Microsoft zaleca, ustaw źródło pliku kodowania na Unicode stronę kodową przed wklejeniem znaków rozszerzonych. Firma Microsoft zaleca, użyj edytora IME lub aplikacji tablicy znaków do generowania znaków rozszerzonych.

**END specyficzny dla Microsoft**

### <a name="basic-execution-character-set"></a>Zestaw znaków wykonania podstawowego

*Zestaw znaków wykonania podstawowego* i *zestaw znaków dwubajtowych wykonania podstawowego* składają się z wszystkich znaków w zestawie znaków podstawowego źródła oraz znaki kontrolne, które reprezentują alertu BACKSPACE, znaku powrotu karetki i znaku null. *Zestaw znaków wykonania* i *zestaw znaków dwubajtowych wykonywania* są nadzbiorami podstawowe zestawy. Obejmują one znaków zdefiniowanych w implementacji źródła poza zestaw znaków podstawowego źródła. Zestaw znaków wykonania jej reprezentacji specyficzne dla ustawień regionalnych.