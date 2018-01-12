---
title: "Ctypedptrmap — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CTypedPtrMap
- AFXTEMPL/CTypedPtrMap
- AFXTEMPL/CTypedPtrMap::GetNextAssoc
- AFXTEMPL/CTypedPtrMap::Lookup
- AFXTEMPL/CTypedPtrMap::RemoveKey
- AFXTEMPL/CTypedPtrMap::SetAt
dev_langs: C++
helpviewer_keywords:
- CTypedPtrMap [MFC], GetNextAssoc
- CTypedPtrMap [MFC], Lookup
- CTypedPtrMap [MFC], RemoveKey
- CTypedPtrMap [MFC], SetAt
ms.assetid: 9f377385-c6e9-4471-8b40-8fe220c50164
caps.latest.revision: "23"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 9056fc73e2718b2a21936c39e630f4d4fddf1eed
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="ctypedptrmap-class"></a>Ctypedptrmap — klasa
Udostępnia bezpieczne "otoki" dla obiektów klasy mapy wskaźnika `CMapPtrToPtr`, `CMapPtrToWord`, `CMapWordToPtr`, i `CMapStringToPtr`.  
  
## <a name="syntax"></a>Składnia  
  
```  
template<class BASE_CLASS, class KEY, class VALUE>  
class CTypedPtrMap : public BASE_CLASS  
```  
  
#### <a name="parameters"></a>Parametry  
 `BASE_CLASS`  
 Klasa podstawowa klasy mapy typizowaną wskaźnika; musi być klasą mapy wskaźnika ( `CMapPtrToPtr`, `CMapPtrToWord`, `CMapWordToPtr`, lub `CMapStringToPtr`).  
  
 `KEY`  
 Klasa Obiekt używany jako klucz do mapy.  
  
 `VALUE`  
 Klasa obiektu przechowywane na mapie.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CTypedPtrMap::GetNextAssoc](#getnextassoc)|Pobiera następnego elementu potrzeby iteracji.|  
|[CTypedPtrMap::Lookup](#lookup)|Zwraca `KEY` na podstawie `VALUE`.|  
|[CTypedPtrMap::RemoveKey](#removekey)|Usuwa element określony przez klucz.|  
|[CTypedPtrMap::SetAt](#setat)|Wstawia element do mapy; zastępuje istniejący element, jeśli dopasowany klucz zostanie znaleziony.|  
  
### <a name="public-operators"></a>Operatory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[[CTypedPtrMap::operator]](#operator_at)|Wstawia element do mapy.|  
  
## <a name="remarks"></a>Uwagi  
 Jeśli używasz `CTypedPtrMap`, funkcji Kontrola typów języka C++ pozwala wyeliminować błędy spowodowane przez wskaźnik niezgodne typy.  
  
 Ponieważ wszystkie `CTypedPtrMap` funkcje są wbudowane, użyj tego szablonu nie znacząco wpływa na rozmiar lub prędkość kodu.  
  
 Aby uzyskać więcej informacji na temat używania `CTypedPtrMap`, zobacz artykuły [kolekcje](../../mfc/collections.md) i [na podstawie szablonu klasy](../../mfc/template-based-classes.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `BASE_CLASS`  
  
 `CTypedPtrMap`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxtempl.h  
  
##  <a name="getnextassoc"></a>CTypedPtrMap::GetNextAssoc  
 Pobiera element mapy pod `rNextPosition`, następnie aktualizuje `rNextPosition` do odwoływania się do następnego elementu na mapie.  
  
```  
void GetNextAssoc(
    POSITION& rPosition,
    KEY& rKey,
    VALUE& rValue) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `rPosition`  
 Określa odwołania do **pozycji** wartość zwrócona przez poprzednie `GetNextAssoc` lub `BASE_CLASS` **:: GetStartPosition** wywołania.  
  
 *KEY*  
 Parametr szablonu określenie typu kluczy mapy.  
  
 `rKey`  
 Określa klucz zwróconego elementu pobrane.  
  
 *WARTOŚĆ*  
 Parametr szablonu określający typ wartości mapy.  
  
 `rValue`  
 Określa wartość elementu pobrane.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja jest najbardziej przydatny w przypadku iteracja przez wszystkie elementy na mapie. Należy pamiętać, że sekwencji pozycji nie jest zawsze taki sam jak wartości klucza sekwencji.  
  
 Jeśli element pobrane przez ostatnie na mapie jest następnie nowa wartość `rNextPosition` ustawiono **NULL**.  
  
 Wywołania tej funkcji wbudowanej `BASE_CLASS` **:: GetNextAssoc**.  
  
##  <a name="lookup"></a>CTypedPtrMap::Lookup  
 `Lookup`używa algorytmu wyznaczania wartości skrótu, aby szybko znaleźć Mapuj element z kluczem takim samym dokładnie.  
  
```  
BOOL Lookup(BASE_CLASS ::BASE_ARG_KEY key, VALUE& rValue) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `BASE_CLASS`  
 Parametr szablonu określający klasą podstawową klasy tej mapy.  
  
 `key`  
 Klucz elementu, który ma być wyszukiwane.  
  
 *WARTOŚĆ*  
 Parametr szablonu określający typ wartości przechowywanych na tej mapie.  
  
 `rValue`  
 Określa wartość elementu pobrane.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli znaleziono element; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Wywołania tej funkcji wbudowanej `BASE_CLASS` **:: wyszukiwania**.  
  
##  <a name="operator_at"></a>[CTypedPtrMap::operator]  
 Ten operator może służyć tylko po lewej stronie instrukcji przypisania (wartością l-value).  
  
```  
VALUE& operator[ ](base_class ::base_arg_key key);
```  
  
### <a name="parameters"></a>Parametry  
 *WARTOŚĆ*  
 Parametr szablonu określający typ wartości przechowywanych na tej mapie.  
  
 `BASE_CLASS`  
 Parametr szablonu określający klasą podstawową klasy tej mapy.  
  
 `key`  
 Klucz elementu do przeszukiwać lub utworzenia na mapie.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli nie ma mapy elementu z określonym kluczem, jest tworzony nowy element. Nie jest równoważna tego operatora nie "po prawej stronie" (r), ponieważ istnieje możliwość, że nie można odnaleźć klucza na mapie. Użyj `Lookup` funkcji członkowskiej dla elementu pobierania.  
  
##  <a name="removekey"></a>CTypedPtrMap::RemoveKey  
 Wywołania funkcji członkowskiej `BASE_CLASS` **:: RemoveKey**.  
  
```  
BOOL RemoveKey(KEY key);
```  
  
### <a name="parameters"></a>Parametry  
 *KEY*  
 Parametr szablonu określenie typu kluczy mapy.  
  
 `key`  
 Klucz elementu do usunięcia.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli wpis został znaleziony i pomyślnie usunął; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Aby uzyskać bardziej szczegółowe uwagi, zobacz [CMapStringToOb::RemoveKey](../../mfc/reference/cmapstringtoob-class.md#removekey).  
  
##  <a name="setat"></a>CTypedPtrMap::SetAt  
 Wywołania funkcji członkowskiej `BASE_CLASS` **:: SetAt**.  
  
```  
void SetAt(KEY key, VALUE newValue);
```  
  
### <a name="parameters"></a>Parametry  
 *KEY*  
 Parametr szablonu określenie typu kluczy mapy.  
  
 `key`  
 Określa wartość klucza newValue.  
  
 `newValue`  
 Określa wskaźnik do obiektu, który jest wartością nowego elementu.  
  
### <a name="remarks"></a>Uwagi  
 Aby uzyskać bardziej szczegółowe uwagi, zobacz [CMapStringToOb::SetAt](../../mfc/reference/cmapstringtoob-class.md#setat).  
  
## <a name="see-also"></a>Zobacz też  
 [Przykładowe MFC ZBIERANIE](../../visual-cpp-samples.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasa CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)   
 [Klasa CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)   
 [Klasa CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)   
 [Klasa CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)
