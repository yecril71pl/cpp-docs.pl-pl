---
title: Operatory bitowe języka C | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/29/2018
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9c5c360246282f8b6062d21061856a57bd2c7194
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="c-bitwise-operators"></a>Operatory bitowe języka C

Operatory bitowe wykonać bitowo- i (**&**), z bitowego OR wyłączne (**^**) i włącznie Alternatywy (**&#124;**) operacje.

## <a name="syntax"></a>Składnia

*I wyrażenia*:  
&nbsp;&nbsp;*equality-expression*  
&nbsp;&nbsp;*Wyrażenia AND* **&** *wyrażenie równości*

*wyrażenie OR-wyłącznie*:  
&nbsp;&nbsp;*Wyrażenia AND*  
&nbsp;&nbsp;*wyrażenie OR-wyłącznie* **^** *i wyrażenia*

*wraz z wartościami granicznymi wyrażenie OR*:  
&nbsp;&nbsp;*wyrażenie OR-na wyłączność*  
&nbsp;&nbsp;*wraz z wartościami granicznymi wyrażenie OR* &#124; *wyłącznie OR-wyrażenie*

Argumenty operacji operatory bitowe muszą mieć typów całkowitych, ale ich typy mogą być różne. Popularne konwersje arytmetyczne; wykonywania tych operatorów Typ wyniku jest typ operandy po konwersji.

Operatory bitowe języka C są opisane poniżej:

|Operator|Opis|
|--------------|-----------------|
|**&**|Operatory- i operatora porównuje każdy bit jego pierwszego operandu na odpowiadający mu bit jej drugi argument operacji. Jeśli oba bity 1, odpowiadający mu bit wynik jest równa 1. W przeciwnym razie odpowiadający mu bit wynik jest równa 0.|
|**^**|Operatora bitowego OR wyłączne porównuje każdy bit jego pierwszego operandu na odpowiadający mu bit jej drugi argument operacji. Jeśli jeden bit ma wartość 0, a inne bit ma wartość 1, odpowiadający mu bit wynik jest równa 1. W przeciwnym razie odpowiadający mu bit wynik jest równa 0.|
|**&#124;**|Operator włącznie Alternatywy porównuje każdy bit jego pierwszego operandu na odpowiadający mu bit jej drugi argument operacji. Jeśli albo bit ma wartość 1, odpowiadający mu bit wynik jest równa 1. W przeciwnym razie odpowiadający mu bit wynik jest równa 0.|

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

Bitowe włącznie lub w drugim przykładzie powoduje wartość 0xABCD (szesnastkowo), podczas gdy lub operator wyłączny w trzecim przykładzie tworzy 0xCD (szesnastkowo).

**Microsoft Specific**

Wyniki operacji na liczb całkowitych ze znakiem jest zdefiniowane w implementacji zgodnie z ANSI C standard. Kompilator Microsoft C Operacje bitowe na liczb całkowitych ze znakiem praca taka sama jak operacje bitowe na liczb całkowitych bez znaku. Na przykład `-16 & 99` może zostać wyrażona w danych binarnych jako

```Expression
  11111111 11110000
& 00000000 01100011
  _________________
  00000000 01100000
```

Wynik iloczynu bitowego AND jest 96 dziesiętną.

**KOŃCOWY określonych firmy Microsoft**

## <a name="see-also"></a>Zobacz także

[Bitowy operator AND: &](../cpp/bitwise-and-operator-amp.md)  
[Operator wyłączny sumy bitowej OR: ^](../cpp/bitwise-exclusive-or-operator-hat.md)  
[Operator włącznie lub Operator:&#124;](../cpp/bitwise-inclusive-or-operator-pipe.md)  