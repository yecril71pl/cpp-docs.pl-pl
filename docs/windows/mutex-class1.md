---
title: Mutex, klasa1 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Mutex
dev_langs:
- C++
helpviewer_keywords:
- Mutex class
ms.assetid: 682a0963-721c-46a2-8871-000e9997505b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b20c270f7848a346d717357f474d89e37ea117a4
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42600031"
---
# <a name="mutex-class1"></a>Mutex, klasa1

Reprezentuje obiekt synchronizacji, który wyłącznie kontroluje zasobu udostępnionego.

## <a name="syntax"></a>Składnia

```cpp
class Mutex : public HandleT<HandleTraits::MutexTraits>
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-typedefs"></a>Publiczne definicje typów

|Nazwa|Opis|
|----------|-----------------|
|`SyncLock`|Synonim dla klasy, która obsługuje synchronicznej blokad.|

### <a name="public-constructor"></a>Konstruktor publiczny

|Nazwa|Opis|
|----------|-----------------|
|[Mutex::Mutex, konstruktor](../windows/mutex-mutex-constructor.md)|Inicjuje nowe wystąpienie klasy **Mutex** klasy.|

### <a name="public-members"></a>Publiczne elementy członkowskie

|Nazwa|Opis|
|----------|-----------------|
|[Mutex::Lock, metoda](../windows/mutex-lock-method.md)|Czeka, aż do bieżącego obiektu lub **Mutex** obiekt skojarzony z określonym dojściem wersji obiektu mutex lub określony limit czasu upłynął.|

### <a name="public-operator"></a>Operator publiczny

|Nazwa|Opis|
|----------|-----------------|
|[Operator Mutex::operator=](../windows/mutex-operator-assign-operator.md)|Przypisuje (ruch) określonego **Mutex** obiekt do bieżącego **Mutex** obiektu.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`Mutex`

## <a name="requirements"></a>Wymagania

**Nagłówek:** corewrappers.h

**Namespace:** Microsoft::wrl:: wrappers

## <a name="see-also"></a>Zobacz też

[Microsoft::WRL::Wrappers, przestrzeń nazw](../windows/microsoft-wrl-wrappers-namespace.md)