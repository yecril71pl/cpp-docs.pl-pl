---
title: Cdaoparameterinfo — struktura | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CDaoParameterInfo
dev_langs:
- C++
helpviewer_keywords:
- CDaoParameterInfo structure [MFC]
- DAO (Data Access Objects), Parameters collection
ms.assetid: 45fd53cd-cb84-4e12-b48d-7f2979f898ad
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8f695d1873a2a5a29393da347567674bf1f08e01
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46433260"
---
# <a name="cdaoparameterinfo-structure"></a>CDaoParameterInfo — Struktura

`CDaoParameterInfo` Struktura zawiera informacje dotyczące obiektu parametr zdefiniowany dla obiektów dostępu do danych (DAO).

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

*m_strName*<br/>
Unikatowej nazwy obiektu parametru. Aby uzyskać więcej informacji zobacz temat "Nazwa właściwości" w Pomocy programu DAO.

*m_nType*<br/>
Wartość, która wskazuje typ danych parametru obiektu. Aby uzyskać listę możliwych wartości, zobacz *m_nType* członkiem [cdaofieldinfo —](../../mfc/reference/cdaofieldinfo-structure.md) struktury. Aby uzyskać więcej informacji zobacz temat "Właściwość Type" w Pomocy programu DAO.

*m_varValue*<br/>
Wartość parametru, przechowywane w [COleVariant](../../mfc/reference/colevariant-class.md) obiektu.

## <a name="remarks"></a>Uwagi

Odwołania do podstawowym i pomocniczym powyżej wskazują, jak informacji jest zwróconych przez [getparameterinfo —](../../mfc/reference/cdaoquerydef-class.md#getparameterinfo) funkcja elementu członkowskiego w klasie `CDaoQueryDef`.

MFC nie hermetyzuje DAO parametr obiektów w klasie. DAO querydef obiektów podstawowych MFC `CDaoQueryDef` obiekty przechowywania parametrów w ich kolekcji parametrów. Dostęp do obiektów parametru w [CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md) obiektu, wywołaj obiektu querydef `GetParameterInfo` funkcję członkowską nazwę określonego parametru lub indeksu w kolekcji parametrów. Możesz użyć [CDaoQueryDef::GetParameterCount](../../mfc/reference/cdaoquerydef-class.md#getparametercount) funkcja elementu członkowskiego w połączeniu z `GetParameterInfo` pętli kolekcji parametrów.

Informacje o pobrane przez [CDaoQueryDef::GetParameterInfo](../../mfc/reference/cdaoquerydef-class.md#getparameterinfo) funkcja członkowska jest przechowywany w `CDaoParameterInfo` struktury. Wywołaj `GetParameterInfo` dla obiektu querydef, w których Kolekcja parametrów jest przechowywany obiekt parametru.

> [!NOTE]
>  Jeśli chcesz pobrać lub ustawić wartości parametru, użyj [GetParamValue](../../mfc/reference/cdaorecordset-class.md#getparamvalue) i [SetParamValue](../../mfc/reference/cdaorecordset-class.md#setparamvalue) funkcji elementów członkowskich klasy `CDaoRecordset`.

`CDaoParameterInfo` definiuje również `Dump` kompilacje funkcja elementu członkowskiego podczas debugowania. Możesz użyć `Dump` do porzucenia zawartość `CDaoParameterInfo` obiektu.

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxdao.h

## <a name="see-also"></a>Zobacz też

[Struktury, style, wywołania zwrotne i mapy komunikatów](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[Klasa CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md)
