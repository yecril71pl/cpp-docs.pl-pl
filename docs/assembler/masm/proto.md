---
title: PROTO
ms.date: 10/22/2018
f1_keywords:
- PROTO
helpviewer_keywords:
- PROTO directive
ms.assetid: 0487ee16-9dc7-43d1-9445-cd1601f5a080
ms.openlocfilehash: 24ec2a9abc6c8b76fc81f6d412019296c53160f4
ms.sourcegitcommit: 9ee5df398bfd30a42739632de3e165874cb675c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74394752"
---
# <a name="proto"></a>PROTO

Prototypuje funkcję lub procedurę. Można wywołać funkcję prototypową przez dyrektywę PROTO za pomocą dyrektywy [Invoke](invoke.md) .

## <a name="syntax"></a>Składnia

> *Label* **proto** ⟦*Distance*⟧ ⟦*Language-Type*⟧ ⟦ __,__ ⟦*Parameter*⟧ __:__ *tag* ... ⟧

### <a name="parameters"></a>Parametry

*etykieta*\
Nazwa funkcji prototypowej.

\ *odległości*
Obowiązkowe Używane w 16-bitowych modelach pamięci do przesłonięcia domyślnego i wskazuje **niemal** lub **daleko** wywołań.

\ *typu języka*
Obowiązkowe Ustawia konwencję wywoływania i nazewnictwa dla procedur i symboli publicznych. Obsługiwane konwencje to:

- 32-bitowy model **płaski** : **C**, **stdcall**

- modele 16-bitowe: **C**, **Basic**, **Pascal**, **Pascal**, **syscall**, **stdcall**

\ *parametru*
Opcjonalna nazwa parametru funkcji.

\ *tagów*
Typ parametru funkcji.

Parametry *parametrów* i *tagów* mogą pojawiać się wiele razy, raz dla każdego przerzuconego argumentu.

## <a name="example"></a>Przykład

Ten przykład pokazuje deklarację **proto** dla funkcji o nazwie `addup3`, która używa **niemal** wywołania do przesłania domyślnego modelu 16-bitowego dla wywołań procedury i używa konwencji wywoływania języka **C** dla parametrów stosu i zwracanych wartości. Przyjmuje dwa argumenty, **słowo** i **vararg**.

```MASM
addup3 PROTO NEAR C, argcount:WORD, arg1:VARARG
```

## <a name="see-also"></a>Zobacz także

[Dokumentacja dyrektyw](directives-reference.md)\
[. Odwołanie do modelu](dot-model.md)
