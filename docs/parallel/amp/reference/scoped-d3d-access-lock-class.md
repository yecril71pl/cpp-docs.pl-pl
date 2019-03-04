---
title: scoped_d3d_access_lock — Klasa
ms.date: 11/04/2016
f1_keywords:
- scoped_d3d_access_lock
- AMPRT/scoped_d3d_access_lock
- AMPRT/concurrency::direct3d::scoped_d3d_access_lock::scoped_d3d_access_lock
ms.assetid: 0ad333e6-9839-4736-a722-16d95d70c4b1
ms.openlocfilehash: e36c3c2cfa9d1b617e377a7e340f98875457bdf1
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57272467"
---
# <a name="scopedd3daccesslock-class"></a>scoped_d3d_access_lock — Klasa

Otoka RAII na blokadę dostępu D3D na obiekcie accelerator_view.

### <a name="syntax"></a>Składnia

```
class scoped_d3d_access_lock;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[scoped_d3d_access_lock Constructor](#ctor)|Przeciążone. Konstruuje `scoped_d3d_access_lock` obiektu. Blokada jest zwalniana, gdy ten obiekt wykracza poza zakres tej asysty.|
|[~ scoped_d3d_access_lock — destruktor](#dtor)|Zwalnia blokadę dostępu D3D dla powiązanego `accelerator_view` obiektu.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[operator=](#operator_eq)|Przejmuje na własność blokadę z innego `scoped_d3d_access_lock`.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`scoped_d3d_access_lock`

## <a name="requirements"></a>Wymagania

**Nagłówek:** amprt.h

**Namespace:** concurrency::direct3d

##  <a name="ctor"></a> scoped_d3d_access_lock

Konstruuje `scoped_d3d_access_lock` obiektu. Blokada jest zwalniana, gdy ten obiekt wykracza poza zakres tej asysty.

```
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
`accelerator_view` Dla blokady do przyjęcia.

*_T*<br/>
`adopt_d3d_access_lock_t` Obiektu.

*_Inne*<br/>
`scoped_d3d_access_lock` Obiektu, z którego należy przenieść istniejącą blokadę.

## <a name="construction"></a>Konstrukcja

[1] Konstruktor uzyskuje blokadę dostępu D3D na danym [accelerator_view](accelerator-view-class.md) obiektu. Konstruowanie bloków, dopóki jest blokada.

[2] Konstruktor przyjmuje blokadę dostępu D3D z danego [accelerator_view](accelerator-view-class.md) obiektu.

[3] Konstruktor przenoszący ma istniejącą blokadę dostępu D3D z innego `scoped_d3d_access_lock` obiektu. Konstrukcje nie są blokowane.

##  <a name="dtor"></a> ~ scoped_d3d_access_lock

Zwalnia blokadę dostępu D3D dla powiązanego `accelerator_view` obiektu.

```
~scoped_d3d_access_lock();
```

## <a name="operator_eq"></a> operator =

Przejmuje na własność blokadę dostępu D3D z innego `scoped_d3d_access_lock` obiektów, zwalniając poprzednią blokadę.

```
scoped_d3d_access_lock& operator= (scoped_d3d_access_lock&& _Other);
```

### <a name="parameters"></a>Parametry

*_Inne*<br/>
Accelerator_view, z którego ma zostać przeniesiona blokada dostępu D3D.

### <a name="return-value"></a>Wartość zwracana

Odwołanie do `scoped_accelerator_view_lock`.

## <a name="see-also"></a>Zobacz także

[Concurrency::direct3d, przestrzeń nazw](concurrency-direct3d-namespace.md)
