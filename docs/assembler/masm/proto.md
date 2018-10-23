---
title: PROTO | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 10/22/2018
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- PROTO
dev_langs:
- C++
helpviewer_keywords:
- PROTO directive
ms.assetid: 0487ee16-9dc7-43d1-9445-cd1601f5a080
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4fd00263f3b4a7ffcf23ccd0501989c0d40c637d
ms.sourcegitcommit: f3a5dc788e62bb36e2d9bc3e62e0aa533422408b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/23/2018
ms.locfileid: "49644066"
---
# <a name="proto"></a>PROTO

Prototypy funkcji lub procedury. Można wywołać funkcji prototypowej przez PROTO — dyrektywa przy użyciu [INVOKE](invoke.md) dyrektywy.

## <a name="syntax"></a>Składnia

> *Etykieta* **PROTO** \[ *odległość*] \[ *langtype*] \[ __,__ \[ *parametru*]__:__*tag*]...

### <a name="parameters"></a>Parametry

*Etykieta*<br/>
Nazwa funkcji prototypowej.

*odległość*<br/>
(Opcjonalnie) Używane w modelach pamięci 16-bitowych można zastąpić to ustawienie domyślne i wskazują **NEAR** lub **DALEKIEGO** wywołania.

*langtype*<br/>
(Opcjonalnie) Określa Konwencję wywoływania i nazewnictwa dla procedur i symboli publicznych. Konwencje obsługiwane są następujące:

- 32-bitowych **PROSTEGO** modelu: **C**, **STDCALL**

- modele 16-bitowych: **C**, **BASIC**, **FORTRAN**, **PASCAL**, **SYSCALL**, **STDCALL**

*Parametr*<br/>
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
