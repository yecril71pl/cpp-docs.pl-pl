---
title: Klasa lock
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- msclr::lock
- msclr.lock
- lock
helpviewer_keywords:
- lock class
ms.assetid: 5123edd9-6aed-497d-9a0b-f4b6d6c0d666
ms.openlocfilehash: 8876810b15a7d2736f2c8ab0ca1f4c6011918a5f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50547137"
---
# <a name="lock-class"></a>Klasa lock

Ta klasa umożliwia zautomatyzowanie biorąc blokady do synchronizowania dostępu do obiektu z wielu wątków.  Gdy konstruowany kupuje blokady i kiedy niszczony jego wersji blokady.

## <a name="syntax"></a>Składnia

```
ref class lock;
```

## <a name="remarks"></a>Uwagi

`lock` jest dostępna tylko w przypadku obiektów CLR i można używać tylko w kodzie CLR.

Wewnętrznie używa klasy blokady <xref:System.Threading.Monitor> do synchronizowania dostępu. Zobacz ten temat, aby uzyskać szczegółowe informacje w synchronizacji.

## <a name="requirements"></a>Wymagania

**Plik nagłówkowy** \<msclr\lock.h >

**Namespace** msclr

## <a name="see-also"></a>Zobacz też

[lock](../dotnet/lock.md)<br/>
[lock, składowe](../dotnet/lock-members.md)