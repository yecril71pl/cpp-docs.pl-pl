---
title: Makra mapy obiektów | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- atlcom/ATL::DECLARE_OBJECT_DESCRIPTION
- atlcom/ATL::OBJECT_ENTRY_AUTO
- atlcom/ATL::OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO
dev_langs:
- C++
ms.assetid: 680087f4-9894-41dd-a79c-6f337e1f13c1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0786ada9a9548fa4e3517cb74fe37e5b7f244be2
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43218651"
---
# <a name="object-map-macros"></a>Makra mapy obiektów
Te makra definiują obiekt map i wpisy.  
  
|||  
|-|-|  
|[DECLARE_OBJECT_DESCRIPTION](#declare_object_description)|Można określić opis tekstowy obiektu klasy, której będzie można wprowadzić w mapie obiektu.|  
|[OBJECT_ENTRY_AUTO](#object_entry_auto)|Wejścia obiektu ATL na mapie obiektów, zaktualizowanie rejestru i tworzy wystąpienie obiektu.|  
|[OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO](#object_entry_non_createable_ex_auto)|Pozwala określić, że zarejestrowane i zainicjować obiekt, ale nie powinien być zewnętrznie utworzone za pomocą `CoCreateInstance`.|  

## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlcom.h  
   
##  <a name="declare_object_description"></a>  DECLARE_OBJECT_DESCRIPTION  
 Można określić opis obiektu klasy.  
  
```
DECLARE_OBJECT_DESCRIPTION( x )
```  
  
### <a name="parameters"></a>Parametry  
 *x*  
 [in] Opis obiektu klasy.  
  
### <a name="remarks"></a>Uwagi  
 ATL wejścia na mapie obiektów za pomocą tego opisu [OBJECT_ENTRY](https://msdn.microsoft.com/abd10ee2-54f0-4f94-9ec2-ddf8f4c8c8cd) makra.  
  
 Implementuje DECLARE_OBJECT_DESCRIPTION `GetObjectDescription` funkcji, która służy do zastępowania [CComCoClass::GetObjectDescription](ccomcoclass-class.md#getobjectdescription) metody.  

  
 `GetObjectDescription` Funkcja jest wywoływana przez `IComponentRegistrar::GetComponents`. `IComponentRegistrar` to interfejs automatyzacji, która umożliwia rejestrowanie i wyrejestrowywanie poszczególne składniki w bibliotece DLL. Po utworzeniu obiektu rejestratora składników za pomocą Kreatora projektu ATL, Kreator automatycznie wdroży `IComponentRegistrar` interfejsu. `IComponentRegistrar` zwykle jest używana przez program Microsoft Transaction Server.  
  
 Aby uzyskać więcej informacji na temat Kreator projektów ATL, zobacz artykuł [Tworzenie projektu ATL](../../atl/reference/creating-an-atl-project.md).  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATL_Windowing#123](../../atl/codesnippet/cpp/object-map-macros_1.h)]  
  
##  <a name="object_entry_auto"></a>  OBJECT_ENTRY_AUTO  
 Wejścia obiektu ATL na mapie obiektów, zaktualizowanie rejestru i tworzy wystąpienie obiektu.  
  
```
OBJECT_ENTRY_AUTO( clsid, class )
```  
  
### <a name="parameters"></a>Parametry  
 *Identyfikator klasy*  
 [in] Identyfikator CLSID klasy COM, zaimplementowany przez klasę C++ o nazwie *klasy*.  
  
 *class*  
 [in] Nazwa klasy języka C++, implementacja klasy COM, reprezentowane przez *clsid*.  
  
### <a name="remarks"></a>Uwagi  
 Makra wejść obiektu są umieszczane w zakresie globalnym w projekcie w celu zapewnienia obsługi rejestracji, inicjowanie i tworzenia klasy.  
  
 OBJECT_ENTRY_AUTO wprowadza wskaźników funkcji, twórca klasy oraz klasy twórcy fabryki klas `CreateInstance` funkcji dla tego obiektu do mapy obiektu ATL wygenerowany automatycznie. Gdy [CAtlComModule::RegisterServer](catlcommodule-class.md#registerserver) jest wywoływana, powoduje zaktualizowanie rejestru systemowego dla każdego obiektu na mapie obiektu.  

  
 W poniższej tabeli opisano sposób uzyskiwania informacji dodany do mapy obiektu z klasy umożliwiającej to makro jako drugi parametr.  
  
|Informacje dotyczące|Uzyskany z|  
|---------------------|-------------------|  
|Rejestracji modelu COM|[Makra rejestru](../../atl/reference/registry-macros.md)|  
|Tworzenie fabryki klas|[Makra fabryki klas](../../atl/reference/aggregation-and-class-factory-macros.md)|  
|Tworzenie wystąpienia|[Makra agregacji](../../atl/reference/aggregation-and-class-factory-macros.md)|  
|Rejestracji kategorii składników|[Makra kategorii](../../atl/reference/category-macros.md)|  
|Poziomie klasy, inicjowanie i oczyszczanie|[ObjectMain](ccomobjectrootex-class.md#objectmain)|  

  
##  <a name="object_entry_non_createable_ex_auto"></a>  OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO  
 Pozwala określić, że zarejestrowane i zainicjować obiekt, ale nie powinien być zewnętrznie utworzone za pomocą `CoCreateInstance`.  
  
```
OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO( clsid, class )
```  
  
### <a name="parameters"></a>Parametry  
 *Identyfikator klasy*  
 [in] Identyfikator CLSID klasy COM, zaimplementowany przez klasę C++ o nazwie *klasy*.  
  
 *class*  
 [in] Nazwa klasy języka C++, implementacja klasy COM, reprezentowane przez *clsid*.  
  
### <a name="remarks"></a>Uwagi  
 Makra wejść obiektu są umieszczane w zakresie globalnym w projekcie w celu zapewnienia obsługi rejestracji, inicjowanie i tworzenia klasy.  
  
 OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO pozwala określić, że zarejestrowane i zainicjować obiektu (zobacz [OBJECT_ENTRY_AUTO](#object_entry_auto) Aby uzyskać więcej informacji), ale nie powinien być utworzone za pomocą `CoCreateInstance`.  
  
## <a name="see-also"></a>Zobacz też  
 [Makra](../../atl/reference/atl-macros.md)
