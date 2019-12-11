---
title: PROTO
ms.date: 12/06/2019
f1_keywords:
- PROTO
helpviewer_keywords:
- PROTO directive
ms.assetid: 0487ee16-9dc7-43d1-9445-cd1601f5a080
ms.openlocfilehash: 9df66b6c89498a2cc1a1864a668b7addfbaf593c
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2019
ms.locfileid: "74987874"
---
# <a name="proto"></a>PROTO

Prototypuje funkcję lub procedurę. Można wywołać funkcję prototypową przez dyrektywę PROTO za pomocą dyrektywy [Invoke](invoke.md) .

## <a name="syntax"></a>Składnia

> *Label* **proto** ⟦*Distance*⟧ ⟦*Language-Type*⟧ ⟦ __,__ ⟦*Parameter*⟧ __:__ *tag* ... ⟧

### <a name="parameters"></a>Parametry

*etykieta*\
Nazwa funkcji prototypowej.

*odległość* (32-bitowa MASM). \
Obowiązkowe Używane w 16-bitowych modelach pamięci do przesłonięcia domyślnego i wskazuje **niemal** lub **daleko** wywołań.

*Typ języka* (tylko 32-bitowy MASM). \
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
