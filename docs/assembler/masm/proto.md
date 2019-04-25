---
title: PROTO
ms.date: 10/22/2018
f1_keywords:
- PROTO
helpviewer_keywords:
- PROTO directive
ms.assetid: 0487ee16-9dc7-43d1-9445-cd1601f5a080
ms.openlocfilehash: 616b6be2a5c191ebc67d61288cb5fa6c183091fa
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62210524"
---
# <a name="proto"></a>PROTO

Prototypy funkcji lub procedury. Można wywołać funkcji prototypowej przez PROTO — dyrektywa przy użyciu [INVOKE](invoke.md) dyrektywy.

## <a name="syntax"></a>Składnia

> *Etykieta* **PROTO** \[ *odległość*] \[ *langtype*] \[ __,__ \[ *parametru*]__:__*tag*]...

### <a name="parameters"></a>Parametry

*Etykieta*<br/>
Nazwa funkcji prototypowej.

*distance*<br/>
(Opcjonalnie) Używane w modelach pamięci 16-bitowych można zastąpić to ustawienie domyślne i wskazują **NEAR** lub **DALEKIEGO** wywołania.

*langtype*<br/>
(Opcjonalnie) Określa Konwencję wywoływania i nazewnictwa dla procedur i symboli publicznych. Konwencje obsługiwane są następujące:

- 32-bitowych **PROSTEGO** modelu: **C**, **STDCALL**

- modele 16-bitowych: **C**, **BASIC**, **FORTRAN**, **PASCAL**, **SYSCALL**, **STDCALL**

*parameter*<br/>
Opcjonalna nazwa parametru funkcji.

*Tag*<br/>
Typ parametru funkcji.

*Parametru* i *tag* parametry mogą pojawiać się wielokrotnie, jeden raz dla każdego przekazany argument.

## <a name="example"></a>Przykład

W tym przykładzie pokazano **PROTO** deklarację funkcji o nazwie `addup3` , który używa **NEAR** wywołanie, aby zastąpić domyślne modelu 16-bitowych dla wywołań procedur i używa **C**Konwencję wywoływania dla stosu parametry i zwracane wartości. Jego przyjmuje dwa argumenty **WORD** i **VARARG**.

```MASM
addup3 PROTO NEAR C, argcount:WORD, arg1:VARARG
```

## <a name="see-also"></a>Zobacz także

[Dokumentacja dyrektyw](directives-reference.md)<br/>
[. Dokumentacja modelu](dot-model.md)<br/>
