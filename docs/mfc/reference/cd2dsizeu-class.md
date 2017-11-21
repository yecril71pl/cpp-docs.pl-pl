---
title: Klasa CD2DSizeU | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CD2DSizeU
- AFXRENDERTARGET/CD2DSizeU
- AFXRENDERTARGET/CD2DSizeU::CD2DSizeU
- AFXRENDERTARGET/CD2DSizeU::IsNull
dev_langs: C++
helpviewer_keywords:
- CD2DSizeU [MFC], CD2DSizeU
- CD2DSizeU [MFC], IsNull
ms.assetid: 6e679ba8-2112-43c3-8275-70b660856f02
caps.latest.revision: "18"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: d6cf0870b993580295edfd050ae0ea25a2640174
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="cd2dsizeu-class"></a>Klasa CD2DSizeU
Otoka dla D2D1_SIZE_U.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CD2DSizeU : public D2D1_SIZE_U;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CD2DSizeU::CD2DSizeU](#cd2dsizeu)|Przeciążone. Konstruuje `CD2DSizeU` obiekt z `D2D1_SIZE_U` obiektu.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CD2DSizeU::IsNull](#isnull)|Zwraca `boolean` wartość, która wskazuje, czy wyrażenie nie zawiera prawidłowych danych ( `null`).|  
  
### <a name="public-operators"></a>Operatory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CD2DSizeU::operator CSize](#operator_csize)|Konwertuje `CD2DSizeU` do `CSize` obiektu.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `D2D1_SIZE_U`  
  
 [CD2DSizeU](../../mfc/reference/cd2dsizeu-class.md)  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxrendertarget.h  
  
##  <a name="cd2dsizeu"></a>CD2DSizeU::CD2DSizeU  
 Tworzy obiekt CD2DSizeU z CSize obiektu.  
  
```  
CD2DSizeU(const CSize& size);  
CD2DSizeU(const D2D1_SIZE_U& size);  
  CD2DSizeU(const D2D1_SIZE_U* size);

 
CD2DSizeU(
    UINT32 cx = 0,  
    UINT32 cy = 0);
```  
  
### <a name="parameters"></a>Parametry  
 `size`  
 Rozmiar źródła  
  
 `cx`  
 szerokość źródła  
  
 `cy`  
 wysokość źródła  
  
##  <a name="isnull"></a>CD2DSizeU::IsNull  
 Zwraca wartość logiczną, wskazującą, czy wyrażenie nie zawiera prawidłowych danych (Null).  
  
```  
BOOL IsNull() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość TRUE, jeśli szerokość i wysokość są puste; w przeciwnym razie wartość FALSE.  
  
##  <a name="operator_csize"></a>CD2DSizeU::operator CSize  
 Konwertuje obiekt CSize CD2DSizeU.  
  
```  
operator CSize();
```   
  
### <a name="return-value"></a>Wartość zwracana  
 Bieżąca wartość rozmiaru D2D.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasy](../../mfc/reference/mfc-classes.md)
