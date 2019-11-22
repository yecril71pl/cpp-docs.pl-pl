---
title: CDaoParameterInfo — Struktura
ms.date: 09/17/2019
f1_keywords:
- CDaoParameterInfo
helpviewer_keywords:
- CDaoParameterInfo structure [MFC]
- DAO (Data Access Objects), Parameters collection
ms.assetid: 45fd53cd-cb84-4e12-b48d-7f2979f898ad
ms.openlocfilehash: 9f96cba8ea43db7e24e834b1de4ffb593b2c6e0d
ms.sourcegitcommit: 069e3833bd821e7d64f5c98d0ea41fc0c5d22e53
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2019
ms.locfileid: "74303490"
---
# <a name="cdaoparameterinfo-structure"></a>CDaoParameterInfo — Struktura

Struktura `CDaoParameterInfo` zawiera informacje o obiekcie parametru zdefiniowanym dla obiektów dostępu do danych (DAO). Element DAO 3,6 jest wersją ostateczną i jest uznawany za przestarzały.

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
Unikatowa nazwa obiektu parametru. Aby uzyskać więcej informacji, zobacz temat "Nazwa właściwości" w pomocy DAO.

*m_nType*<br/>
Wartość, która wskazuje typ danych obiektu parametru. Listę możliwych wartości można znaleźć w *m_nType* składowej struktury [CDaoFieldInfo —](../../mfc/reference/cdaofieldinfo-structure.md) . Aby uzyskać więcej informacji, zobacz temat "Type Property" w pomocy DAO.

*m_varValue*<br/>
Wartość parametru przechowywana w obiekcie [COleVariant](../../mfc/reference/colevariant-class.md) .

## <a name="remarks"></a>Uwagi

Odwołania do podstawowych i pomocniczych powyżej wskazują, jak informacje są zwracane przez funkcję elementu członkowskiego [GetParameterInfo](../../mfc/reference/cdaoquerydef-class.md#getparameterinfo) w klasie `CDaoQueryDef`.

MFC nie hermetyzuje obiektów parametrów DAO w klasie. Obiekty DAO querydef powiązane z klasą MFC `CDaoQueryDef` obiekty przechowują parametry w kolekcjach parametrów. Aby uzyskać dostęp do obiektów parametrów w obiekcie [CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md) , wywołaj funkcję członkowską `GetParameterInfo` obiektu querydef dla określonej nazwy parametru lub indeksu do kolekcji Parameters. Można użyć funkcji składowej [CDaoQueryDef:: GetParameterCount](../../mfc/reference/cdaoquerydef-class.md#getparametercount) w połączeniu z `GetParameterInfo` do pętli w kolekcji Parameters.

Informacje pobierane przez funkcję członkowską [CDaoQueryDef:: GetParameterInfo](../../mfc/reference/cdaoquerydef-class.md#getparameterinfo) są przechowywane w strukturze `CDaoParameterInfo`. Wywołaj `GetParameterInfo` dla obiektu querydef, w której Kolekcja parametrów jest przechowywany obiekt parametru.

> [!NOTE]
>  Jeśli chcesz uzyskać lub ustawić tylko wartość parametru, użyj funkcji składowych [GetParamValue](../../mfc/reference/cdaorecordset-class.md#getparamvalue) i [SetParamValue](../../mfc/reference/cdaorecordset-class.md#setparamvalue) klasy `CDaoRecordset`.

`CDaoParameterInfo` również definiuje funkcję członkowską `Dump` w kompilacjach debugowania. Aby zrzucić zawartość obiektu `CDaoParameterInfo`, można użyć `Dump`.

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxdao. h

## <a name="see-also"></a>Zobacz także

[Struktury, style, wywołania zwrotne i mapy komunikatów](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[Klasa CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md)
