---
title: scoped_d3d_access_lock — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-amp
ms.topic: reference
f1_keywords:
- scoped_d3d_access_lock
- AMPRT/scoped_d3d_access_lock
- AMPRT/concurrency::direct3d::scoped_d3d_access_lock::scoped_d3d_access_lock
dev_langs:
- C++
ms.assetid: 0ad333e6-9839-4736-a722-16d95d70c4b1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0053fa89139ac806a3d8ae0572cd053dd6bec72c
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
ms.locfileid: "33688144"
---
# <a name="scopedd3daccesslock-class"></a>scoped_d3d_access_lock — Klasa
RAII otoki dla D3D blokady dostępu do obiektu accelerator_view.  
  
### <a name="syntax"></a>Składnia  
  
```  
class scoped_d3d_access_lock;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[scoped_d3d_access_lock Constructor](#ctor)|Przeciążone. Konstruuje `scoped_d3d_access_lock` obiektu. Blokada jest zwalniany, kiedy ten obiekt wykracza poza zakres.|  
|[~ scoped_d3d_access_lock — destruktor](#dtor)|Zwalnia blokadę dostępu D3D na skojarzonym `accelerator_view` obiektu.|  
  
### <a name="public-operators"></a>Operatory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[operator=](#operator_eq)|Przejmuje blokady z innego `scoped_d3d_access_lock`.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `scoped_d3d_access_lock`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** amprt.h  
  
 **Namespace:** CONCURRENCY::Direct3D —  

##  <a name="ctor"></a> scoped_d3d_access_lock 

 Konstruuje `scoped_d3d_access_lock` obiektu. Blokada jest zwalniany, kiedy ten obiekt wykracza poza zakres.  
 
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
 `_Av`  
 `accelerator_view` Blokady do przyjęcia.  
  
 `_T`  
 `adopt_d3d_access_lock_t` Obiektu.  
  
 `_Other`  
 `scoped_d3d_access_lock` Obiektu, z którego można przenieść istniejącą blokadę.  
  
## <a name="construction"></a>Konstrukcji  
 [1] Konstruktor  
 Uzyskuje blokadę D3D dostępu na danym [accelerator_view](accelerator-view-class.md) obiektu. Bloki konstrukcji, dopóki blokada jest uzyskiwana.  
  
 [2] Konstruktor  
 Przyjmuje D3D blokady dostępu z danego [accelerator_view](accelerator-view-class.md) obiektu.  
  
 [3] Konstruktor przenoszenia  
 Trwa istniejącą blokadę dostępu D3D z innego `scoped_d3d_access_lock` obiektu. Konstrukcja nie są blokowane.  

  
##  <a name="dtor"></a> ~ scoped_d3d_access_lock 

 Zwalnia blokadę dostępu D3D na skojarzonym `accelerator_view` obiektu.  
  
```  
~scoped_d3d_access_lock();
```  
## <a name="operator_eq"></a> operator = 

Przejmuje D3D blokady dostępu z innego `scoped_d3d_access_lock` obiektu zwolnienie blokady poprzedniej.  
 
```  
scoped_d3d_access_lock& operator= (scoped_d3d_access_lock&& _Other);
```  
  
### <a name="parameters"></a>Parametry  
 `_Other`  
 Accelerator_view, z którą ma zostać przeniesiony blokowania dostępu D3D.  
  
### <a name="return-value"></a>Wartość zwracana  
 Odwołanie do tego `scoped_accelerator_view_lock`.  

## <a name="see-also"></a>Zobacz też  
 [Concurrency::direct3d, przestrzeń nazw](concurrency-direct3d-namespace.md)
