---
title: "Cdaoparameterinfo — struktura | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: CDaoParameterInfo
dev_langs: C++
helpviewer_keywords:
- CDaoParameterInfo structure [MFC]
- DAO (Data Access Objects), Parameters collection
ms.assetid: 45fd53cd-cb84-4e12-b48d-7f2979f898ad
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 68e2eff68eb4a5ae2d7868929bca169e399a7347
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="cdaoparameterinfo-structure"></a>CDaoParameterInfo — Struktura
`CDaoParameterInfo` Struktura zawiera informacje dotyczące obiektu parametru zdefiniowany dla obiektów dostępu do danych (DAO).  
  
## <a name="syntax"></a>Składnia  
  
```  
struct CDaoParameterInfo  
{  
    CString m_strName;       // Primary  
    short m_nType;           // Primary  
    ColeVariant m_varValue;  // Secondary  
};  
```  
  
#### <a name="parameters"></a>Parametry  
 `m_strName`  
 Unikatowej nazwy obiektu parameter. Aby uzyskać więcej informacji zobacz temat "Właściwości Name" w pomocy DAO.  
  
 `m_nType`  
 Wartość, która określa typ danych parametru obiektu. Aby uzyskać listę możliwych wartości, zobacz `m_nType` członkiem [cdaofieldinfo —](../../mfc/reference/cdaofieldinfo-structure.md) struktury. Aby uzyskać więcej informacji zobacz temat "Właściwość Type" w pomocy DAO.  
  
 *m_varValue*  
 Wartość parametru, przechowywane w [COleVariant](../../mfc/reference/colevariant-class.md) obiektu.  
  
## <a name="remarks"></a>Uwagi  
 Odwołania do podstawowego i zapasowego powyżej wskazują, jak informacje zwracane przez [GetParameterInfo](../../mfc/reference/cdaoquerydef-class.md#getparameterinfo) funkcji członkowskiej klasy `CDaoQueryDef`.  
  
 MFC nie hermetyzować DAO parametru obiektów w klasie. DAO querydef obiektów MFC podstawowej `CDaoQueryDef` Parametry sklepu obiekty w kolekcjach ich parametrów. Dostęp do obiektów parametru w [CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md) obiekt, należy wywołać obiekt querydef `GetParameterInfo` funkcji członkowskiej dla określonego parametru nazwę lub indeks w kolekcji parametrów. Można użyć [CDaoQueryDef::GetParameterCount](../../mfc/reference/cdaoquerydef-class.md#getparametercount) funkcji członkowskiej w połączeniu z `GetParameterInfo` pętli kolekcji parametrów.  
  
 Informacje o pobrane przez [CDaoQueryDef::GetParameterInfo](../../mfc/reference/cdaoquerydef-class.md#getparameterinfo) funkcja członkowska jest przechowywany w `CDaoParameterInfo` struktury. Wywołanie `GetParameterInfo` w kolekcji parametrów, których są przechowywane obiektu parameter obiektu querydef.  
  
> [!NOTE]
>  Jeśli chcesz pobrać lub ustawić wartości parametru, użyj [GetParamValue](../../mfc/reference/cdaorecordset-class.md#getparamvalue) i [SetParamValue](../../mfc/reference/cdaorecordset-class.md#setparamvalue) funkcji elementów członkowskich klasy `CDaoRecordset`.  
  
 `CDaoParameterInfo`definiuje również `Dump` kompilacje funkcji członkowskiej podczas debugowania. Można użyć `Dump` do zrzutu zawartość `CDaoParameterInfo` obiektu.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxdao.h  
  
## <a name="see-also"></a>Zobacz też  
 [Struktury, style, wywołania zwrotne i mapy komunikatów](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [Klasa CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md)
