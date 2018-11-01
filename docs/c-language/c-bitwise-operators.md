---
title: Operatory bitowe języka C
ms.date: 01/29/2018
helpviewer_keywords:
- '| operator, bitwise operators'
- bitwise operators, Visual C
- bitwise operators
- operators [C], bitwise
- ^ operator, bitwise operators
- AND operator
- ampersand operator (&)
- ^ operator
- '& operator, bitwise operators'
ms.assetid: e22127b1-9a2d-4876-b01d-c8f72cec3317
ms.openlocfilehash: 2133aaa5faa0f4bef7391fb5c0e7e0eb51fd4e69
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50543376"
---
# <a name="c-bitwise-operators"></a>Operatory bitowe języka C

Operatory bitowe wykonać alternatywy bitowej- i (**&**), bitowe OR wyłączne (**^**), a włącznie — Alternatywy bitowej (**&#124;**) operacje.

## <a name="syntax"></a>Składnia

*Wyrażenia i*: &nbsp; &nbsp; *wyrażenie równości* &nbsp; &nbsp; *i wyrażenie* **&** *wyrażenie równości*

*wyłączny OR wyrażenia*: &nbsp; &nbsp; *i wyrażenie* &nbsp; &nbsp; *wyłączny OR wyrażenia* **^** *Wyrażenia AND*

*wyrażenie włączny OR*: &nbsp; &nbsp; *wyłączny OR wyrażenia* &nbsp; &nbsp; *włącznie wyrażenie OR* &#124; *wyłączny OR wyrażenia*

Operandy operatory bitowe muszą mieć typów całkowitych, ale ich typy mogą być różne. Te operatory wykonywać popularne konwersje arytmetyczne; Typ wyniku jest typem operandu po konwersji.

Operatory bitowe języka C zostały opisane poniżej:

|Operator|Opis|
|--------------|-----------------|
|**&**|Operatora testu koniunkcji — i operator porównuje każdy bit pierwszy argument operacji na odpowiadający mu bit drugim argumentem. Jeśli oba bity są 1, odpowiadający mu bit wynik jest równa 1. W przeciwnym razie odnośny bit wynik jest równa 0.|
|**^**|Operator bitowy OR wyłączne porównuje każdy bit pierwszy argument operacji na odpowiadający mu bit drugim argumentem. Jeśli jeden bit ma wartość 0, a inne bit ma wartość 1, odpowiadający mu bit wynik jest równa 1. W przeciwnym razie odnośny bit wynik jest równa 0.|
|**&#124;**|Operator włącznie — Alternatywy porównuje każdy bit pierwszy argument operacji na odpowiadający mu bit drugim argumentem. Jeśli bit albo ma wartość 1, odpowiadający mu bit wynik jest równa 1. W przeciwnym razie odnośny bit wynik jest równa 0.|

## <a name="examples"></a>Przykłady

Deklaracje te są używane następujące trzy przykłady:

```C
short i = 0xAB00;
short j = 0xABCD;
short n;

n = i & j;
```

Wynik przypisane do `n` w tym pierwszym przykładzie jest taka sama jak `i` (0xAB00 szesnastkowym).

```C
n = i | j;

n = i ^ j;
```

Bitowe alternatywne OR w drugim przykładzie powoduje wartość 0xABCD (szesnastkowo), podczas gdy lub wyłączny sumy bitowej w przykładzie trzeci tworzy wypełniania wartościami 0xCD (szesnastkowo).

**Microsoft Specific**

Wyniki operacja bitowa na liczby całkowite ze znakiem zależy od implementacji zgodnie ze standardu ANSI C. Kompilator Microsoft C: Operacje bitowe na liczby całkowite ze znakiem praca taka sama jak operacje bitowe na liczb całkowitych bez znaku. Na przykład `-16 & 99` mogą być wyrażone w danych binarnych jako

```Expression
  11111111 11110000
& 00000000 01100011
  _________________
  00000000 01100000
```

Bitowe AND powstaje 96 dziesiętną.

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz także

[Bitowy operator AND: &](../cpp/bitwise-and-operator-amp.md)<br/>
[Operator wyłączny sumy bitowej OR: ^](../cpp/bitwise-exclusive-or-operator-hat.md)<br/>
[Bitowe alternatywne OR — Operator:&#124;](../cpp/bitwise-inclusive-or-operator-pipe.md)