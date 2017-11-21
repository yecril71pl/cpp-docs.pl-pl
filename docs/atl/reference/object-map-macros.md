---
title: Makra mapy obiekt | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- atlcom/ATL::DECLARE_OBJECT_DESCRIPTION
- atlcom/ATL::OBJECT_ENTRY_AUTO
- atlcom/ATL::OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO
dev_langs: C++
ms.assetid: 680087f4-9894-41dd-a79c-6f337e1f13c1
caps.latest.revision: "16"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 8c1547f4d78c599ef0e272e8e2e881430c72ced1
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="object-map-macros"></a>Makra mapy obiektu
Te makra zdefiniuj map obiekt i wpisów.  
  
|||  
|-|-|  
|[DECLARE_OBJECT_DESCRIPTION](#declare_object_description)|Można określić opis tekstowy obiektu klasy, który będzie wprowadzany do mapy obiektu.|  
|[OBJECT_ENTRY_AUTO](#object_entry_auto)|Wejścia obiekt ATL Mapa obiektów, aktualizuje rejestr i tworzy wystąpienie obiektu.|  
|[OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO](#object_entry_non_createable_ex_auto)|Umożliwia określenie, że zarejestrowane i zainicjować obiektu, ale nie powinien być zewnętrznie możliwość utworzenia za pośrednictwem `CoCreateInstance`.|  

## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlcom.h  
   
##  <a name="declare_object_description"></a>DECLARE_OBJECT_DESCRIPTION  
 Można określić opis dla obiekt klasy.  
  
```
DECLARE_OBJECT_DESCRIPTION( x )
```  
  
### <a name="parameters"></a>Parametry  
 *x*  
 [in] Opis obiektu klasy.  
  
### <a name="remarks"></a>Uwagi  
 ATL wejścia mapy obiektu przez ten opis [OBJECT_ENTRY](http://msdn.microsoft.com/en-us/abd10ee2-54f0-4f94-9ec2-ddf8f4c8c8cd) makra.  
  
 `DECLARE_OBJECT_DESCRIPTION`implementuje `GetObjectDescription` funkcja, która służy do zastępowania [CComCoClass::GetObjectDescription](ccomcoclass-class.md#getobjectdescription) metody.  

  
 `GetObjectDescription` Funkcja jest wywoływana przez **IComponentRegistrar::GetComponents**. **IComponentRegistrar** jest interfejsem automatyzacji, która pozwala na rejestrowanie i wyrejestrowywanie pojedynczych składników w bibliotece DLL. Podczas tworzenia obiektu rejestratora składników przy użyciu kreatora Projekt ATL, Kreator automatycznie wykona **IComponentRegistrar** interfejsu. **IComponentRegistrar** jest zwykle używany przez program Microsoft Transaction Server.  
  
 Aby uzyskać więcej informacji o Kreatorze Projekt ATL, zobacz artykuł [tworzenie Projekt ATL](../../atl/reference/creating-an-atl-project.md).  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATL_Windowing#123](../../atl/codesnippet/cpp/object-map-macros_1.h)]  
  
##  <a name="object_entry_auto"></a>OBJECT_ENTRY_AUTO  
 Wejścia obiekt ATL Mapa obiektów, aktualizuje rejestr i tworzy wystąpienie obiektu.  
  
```
OBJECT_ENTRY_AUTO( clsid, class )
```  
  
### <a name="parameters"></a>Parametry  
 `clsid`  
 [in] Identyfikator CLSID dla klasy COM, zaimplementowany przez klasę C++ o nazwie `class`.  
  
 `class`  
 [in] Nazwa klasy C++ implementującej klasy COM reprezentowany przez `clsid`.  
  
### <a name="remarks"></a>Uwagi  
 Obiekt wpisu makra są umieszczane w globalnym zakresie w projekcie w celu zapewnienia obsługi rejestracji, inicjowanie i Tworzenie klasy.  
  
 `OBJECT_ENTRY_AUTO`wprowadza wskaźników funkcji klasy creator oraz klasy twórcy fabryki klasy `CreateInstance` funkcji dla tego obiektu do mapy obiektu ATL wygenerowany automatycznie. Gdy [CAtlComModule::RegisterServer](catlcommodule-class.md#registerserver) jest wywoływana, aktualizacji rejestru systemowego dla każdego obiektu w mapie obiektu.  

  
 W poniższej tabeli opisano sposób uzyskiwania informacji dodany do mapy obiekt z klasy nadawane to makro jako drugiego parametru.  
  
|Informacje o|Uzyskane z|  
|---------------------|-------------------|  
|Rejestracji modelu COM|[Makra rejestru](../../atl/reference/registry-macros.md)|  
|Tworzenie fabryki klas|[Makra fabryki klas](../../atl/reference/aggregation-and-class-factory-macros.md)|  
|Tworzenie wystąpienia|[Makra agregacji](../../atl/reference/aggregation-and-class-factory-macros.md)|  
|Składnik kategorii rejestracji|[Makra kategorii](../../atl/reference/category-macros.md)|  
|Klasa poziom inicjowanie i oczyszczanie|[ObjectMain](ccomobjectrootex-class.md#objectmain)|  

  
##  <a name="object_entry_non_createable_ex_auto"></a>OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO  
 Umożliwia określenie, że zarejestrowane i zainicjować obiektu, ale nie powinien być zewnętrznie możliwość utworzenia za pośrednictwem `CoCreateInstance`.  
  
```
OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO( clsid, class )
```  
  
### <a name="parameters"></a>Parametry  
 `clsid`  
 [in] Identyfikator CLSID dla klasy COM, zaimplementowany przez klasę C++ o nazwie `class`.  
  
 `class`  
 [in] Nazwa klasy C++ implementującej klasy COM reprezentowany przez `clsid`.  
  
### <a name="remarks"></a>Uwagi  
 Obiekt wpisu makra są umieszczane w globalnym zakresie w projekcie w celu zapewnienia obsługi rejestracji, inicjowanie i Tworzenie klasy.  
  
 `OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO`Umożliwia określenie, że zarejestrowane i zainicjować obiektu (zobacz [OBJECT_ENTRY_AUTO](#object_entry_auto) Aby uzyskać więcej informacji), ale nie należy tworzyć za pomocą `CoCreateInstance`.  
  
## <a name="see-also"></a>Zobacz też  
 [Makra](../../atl/reference/atl-macros.md)
