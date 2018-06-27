---
title: Klasa CD2DSizeF | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CD2DSizeF
- AFXRENDERTARGET/CD2DSizeF
- AFXRENDERTARGET/CD2DSizeF::CD2DSizeF
- AFXRENDERTARGET/CD2DSizeF::IsNull
dev_langs:
- C++
helpviewer_keywords:
- CD2DSizeF [MFC], CD2DSizeF
- CD2DSizeF [MFC], IsNull
ms.assetid: f486a1e1-997d-4286-8cb9-26369dc82055
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e939d189d991ef234e940b272291c2da6c931684
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/26/2018
ms.locfileid: "36954481"
---
# <a name="cd2dsizef-class"></a>Klasa CD2DSizeF
Otoka dla D2D1_SIZE_F.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CD2DSizeF : public D2D1_SIZE_F;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CD2DSizeF::CD2DSizeF](#cd2dsizef)|Przeciążone. Konstruuje `CD2DSizeF` obiekt z `D2D1_SIZE_F` obiektu.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CD2DSizeF::IsNull](#isnull)|Zwraca **logiczna** wartość, która wskazuje, czy wyrażenie nie zawiera prawidłowych danych ( **null**).|  
  
### <a name="public-operators"></a>Operatory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CD2DSizeF::operator CSize](#operator_csize)|Konwertuje `CD2DSizeF` do `CSize` obiektu.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `D2D1_SIZE_F`  
  
 [CD2DSizeF](../../mfc/reference/cd2dsizef-class.md)  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxrendertarget.h  
  
##  <a name="cd2dsizef"></a>  CD2DSizeF::CD2DSizeF  
 Tworzy obiekt CD2DSizeF z CSize obiektu.  
  
```  
CD2DSizeF(const CSize& size);  
CD2DSizeF(const D2D1_SIZE_F& size);  
  CD2DSizeF(const D2D1_SIZE_F* size);

 
CD2DSizeF(
    FLOAT cx = 0.,  
    FLOAT cy = 0.);
```  
  
### <a name="parameters"></a>Parametry  
 *Rozmiar*  
 Rozmiar źródła  
  
 *CX*  
 szerokość źródła  
  
 *CY*  
 wysokość źródła  
  
##  <a name="isnull"></a>  CD2DSizeF::IsNull  
 Zwraca wartość logiczną, wskazującą, czy wyrażenie nie zawiera prawidłowych danych (Null).  
  
```  
BOOL IsNull() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość TRUE, jeśli szerokość i wysokość są puste; w przeciwnym razie wartość FALSE.  
  
##  <a name="operator_csize"></a>  CD2DSizeF::operator CSize  
 Konwertuje obiekt CSize CD2DSizeF.  
  
```  
operator CSize();
```   
  
### <a name="return-value"></a>Wartość zwracana  
 Bieżąca wartość rozmiaru D2D.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasy](../../mfc/reference/mfc-classes.md)
