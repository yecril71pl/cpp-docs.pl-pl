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
ms.openlocfilehash: 50be8ae38f21d0a9f46c180abf179e1358b707cd
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80168776"
---
# <a name="c-bitwise-operators"></a>Operatory bitowe języka C

Operatory bitowe wykonują operacje bitowe-i ( **&** ), bitowe wykluczające lub ( **^** ) i bitowe lub ( **&#124;** ).

## <a name="syntax"></a>Składnia

*And-Expression*: &nbsp;&nbsp;*wyrażenia równości* &nbsp;&nbsp;*i-Expression* **&** *wyrażenie równości*

*wyłączne lub wyrażeniu*: &nbsp;&nbsp;*i-Expression* &nbsp;&nbsp;z *wyłączeniem lub-* Expression **^** *i-Expression*

*włączne lub wyrażeniu*: &nbsp;&nbsp;*wyłączny lub wyrażeniu* &nbsp;&nbsp;*włącznie* &#124; lub-Expression *-lub-* Expression

Operandy operatorów bitowych muszą mieć typy całkowite, ale ich typy mogą być różne. Operatory te wykonują zwykle konwersje arytmetyczne; Typ wyniku jest typem operandów po konwersji.

Operatory bitowe języka C są opisane poniżej:

|Operator|Opis|
|--------------|-----------------|
|**&**|Operator koniunkcji bitowej porównuje każdy bit pierwszego operandu z odpowiadającym mu bitem drugiego operandu. Jeśli obie bity są 1, odpowiedni bit wynikowy jest ustawiony na 1. W przeciwnym razie odpowiedni bit wynikowy jest ustawiony na 0.|
|**^**|Operator z wyłączeniem bitowym lub porównuje każdy bit pierwszego operandu z odpowiadającym mu bitem drugiego operandu. Jeśli jeden bit ma wartość 0, a drugi bit to 1, odpowiedni bit wynikowy jest ustawiony na 1. W przeciwnym razie odpowiedni bit wynikowy jest ustawiony na 0.|
|**&#124;**|Operator "bitowego" lub "porównujący każdy bit pierwszego operandu z odpowiadającym mu bitem drugiego operandu. Jeśli jeden z bitów to 1, odpowiedni bit wynikowy jest ustawiony na 1. W przeciwnym razie odpowiedni bit wynikowy jest ustawiony na 0.|

## <a name="examples"></a>Przykłady

Te deklaracje są używane w następujących trzech przykładach:

```C
short i = 0xAB00;
short j = 0xABCD;
short n;

n = i & j;
```

Wynik przypisany do `n` w tym pierwszym przykładzie jest taki sam jak `i` (0xAB00 w formacie szesnastkowym).

```C
n = i | j;

n = i ^ j;
```

Bitowe lub w drugim przykładzie wynikiem jest wartość 0xABCD (szesnastkowo), natomiast w przypadku bitowego wyłącznych lub w trzecim przykładzie powstaje 0xCD (szesnastkowo).

**Specyficzne dla firmy Microsoft**

Wyniki operacji bitowej dla liczb całkowitych ze znakiem są zdefiniowane w implementacji zgodnej ze standardem ANSI C. W przypadku kompilatora języka Microsoft C operacje bitowe w podpisanych liczbach całkowitych działają tak samo jak operacje bitowe w liczbach całkowitych bez znaku. Na przykład `-16 & 99` może być wyrażona jako plik binarny jako

```Expression
  11111111 11110000
& 00000000 01100011
  _________________
  00000000 01100000
```

Wynik bitowy i to 96 dziesiętny.

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz też

[Bitowy operator AND: &](../cpp/bitwise-and-operator-amp.md)<br/>
[Operator wyłączny sumy bitowej OR: ^](../cpp/bitwise-exclusive-or-operator-hat.md)<br/>
[Operator włączny bitowego or:&#124;](../cpp/bitwise-inclusive-or-operator-pipe.md)
