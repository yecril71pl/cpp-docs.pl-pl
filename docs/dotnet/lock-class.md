---
title: Klasa Lock | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- msclr::lock
- msclr.lock
- lock
dev_langs:
- C++
helpviewer_keywords:
- lock class
ms.assetid: 5123edd9-6aed-497d-9a0b-f4b6d6c0d666
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 7ef0887ca3eec7510717aab21ba4c6c7aba98d25
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46380298"
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