---
title: scoped_d3d_access_lock — Klasa
ms.date: 11/04/2016
f1_keywords:
- scoped_d3d_access_lock
- AMPRT/scoped_d3d_access_lock
- AMPRT/concurrency::direct3d::scoped_d3d_access_lock::scoped_d3d_access_lock
ms.assetid: 0ad333e6-9839-4736-a722-16d95d70c4b1
ms.openlocfilehash: b5a2d9dab9cba7b19fa0d0b1627f653f2c7fdc57
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/11/2020
ms.locfileid: "77126399"
---
# <a name="scoped_d3d_access_lock-class"></a>scoped_d3d_access_lock — Klasa

Otoka RAII na blokadę dostępu D3D na obiekcie accelerator_view.

## <a name="syntax"></a>Składnia

```cpp
class scoped_d3d_access_lock;
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Konstruktory publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[Konstruktor scoped_d3d_access_lock](#ctor)|Przeciążone. Konstruuje obiekt `scoped_d3d_access_lock`. Blokada jest wydana, gdy ten obiekt wykracza poza zakres.|
|[~ scoped_d3d_access_lock destruktor](#dtor)|Zwalnia blokadę dostępu D3D dla skojarzonego obiektu `accelerator_view`.|

### <a name="public-operators"></a>Operatory publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[operator =](#operator_eq)|Przejmuje na własność blokadę z innego `scoped_d3d_access_lock`.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`scoped_d3d_access_lock`

## <a name="requirements"></a>Wymagania

**Nagłówek:** amprt. h

**Przestrzeń nazw:** concurrency::d irect3d

## <a name="ctor"></a>scoped_d3d_access_lock

Konstruuje obiekt `scoped_d3d_access_lock`. Blokada jest wydana, gdy ten obiekt wykracza poza zakres.

```cpp
explicit scoped_d3d_access_lock(// [1] constructor
    accelerator_view& _Av);

explicit scoped_d3d_access_lock(// [2] constructor
    accelerator_view& _Av,
    adopt_d3d_access_lock_t _T);

scoped_d3d_access_lock(// [3] move constructor
    scoped_d3d_access_lock&& _Other);
```

### <a name="parameters"></a>Parametry

*_Av*<br/>
`accelerator_view` do zastosowania blokady.

*_T*<br/>
Obiekt `adopt_d3d_access_lock_t`.

*_Other*<br/>
Obiekt `scoped_d3d_access_lock`, z którego ma zostać przeniesiona istniejąca blokada.

## <a name="construction"></a>Zrekonstruowan

[1] Konstruktor uzyskuje blokadę dostępu D3D dla danego obiektu [accelerator_view](accelerator-view-class.md) . Bloki konstrukcyjne do momentu uzyskania blokady.

[2] Konstruktor przyjmuje blokadę dostępu D3D z danego obiektu [accelerator_view](accelerator-view-class.md) .

[3] Konstruktor przenoszenia pobiera istniejącą blokadę dostępu D3D z innego obiektu `scoped_d3d_access_lock`. Konstrukcja nie jest blokowana.

## <a name="dtor"></a>~ scoped_d3d_access_lock

Zwalnia blokadę dostępu D3D dla skojarzonego obiektu `accelerator_view`.

```cpp
~scoped_d3d_access_lock();
```

## <a name="operator_eq"></a>operator =

Przejmuje na własność blokadę dostępu D3D z innego obiektu `scoped_d3d_access_lock`, zwalniając poprzednią blokadę.

```cpp
scoped_d3d_access_lock& operator= (scoped_d3d_access_lock&& _Other);
```

### <a name="parameters"></a>Parametry

*_Other*<br/>
Accelerator_view, z którego ma zostać przeniesiona blokada dostępu D3D.

### <a name="return-value"></a>Wartość zwrócona

Odwołanie do tego `scoped_accelerator_view_lock`.

## <a name="see-also"></a>Zobacz też

[Concurrency::direct3d, przestrzeń nazw](concurrency-direct3d-namespace.md)
