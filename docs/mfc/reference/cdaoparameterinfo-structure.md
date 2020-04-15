---
title: CDaoParameterInfo — Struktura
ms.date: 09/17/2019
f1_keywords:
- CDaoParameterInfo
helpviewer_keywords:
- CDaoParameterInfo structure [MFC]
- DAO (Data Access Objects), Parameters collection
ms.assetid: 45fd53cd-cb84-4e12-b48d-7f2979f898ad
ms.openlocfilehash: 6d594bbeec34e400eb074c136e3467e78b35c4ee
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368978"
---
# <a name="cdaoparameterinfo-structure"></a>CDaoParameterInfo — Struktura

Struktura `CDaoParameterInfo` zawiera informacje o obiekcie parametru zdefiniowanym dla obiektów dostępu do danych (DAO). DAO 3.6 jest ostateczną wersją i jest uważana za przestarzałą.

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
Unikatowa nazwa obiektu parametru. Aby uzyskać więcej informacji, zobacz temat "Właściwość nazwy" w Pomocy DAO.

*m_nType*<br/>
Wartość wskazująca typ danych obiektu parametru. Aby uzyskać listę możliwych wartości, zobacz *m_nType* element członkowski struktury [CDaoFieldInfo.](../../mfc/reference/cdaofieldinfo-structure.md) Aby uzyskać więcej informacji, zobacz temat "Typ właściwości" w Pomocy DAO.

*m_varValue*<br/>
Wartość parametru, przechowywane w [COleVariant](../../mfc/reference/colevariant-class.md) obiektu.

## <a name="remarks"></a>Uwagi

Odwołania do podstawowych i pomocniczych powyżej wskazują, jak informacje są zwracane `CDaoQueryDef`przez Funkcję elementu członkowskiego [GetParameterInfo](../../mfc/reference/cdaoquerydef-class.md#getparameterinfo) w klasie .

MFC nie hermetyzuje obiektów parametru DAO w klasie. Obiekty DAO querydef `CDaoQueryDef` leżące u podstaw obiektów MFC przechowują parametry w swoich kolekcjach Parameters. Aby uzyskać dostęp do obiektów parametrów w obiekcie [CDaoQueryDef,](../../mfc/reference/cdaoquerydef-class.md) wywołaj funkcję `GetParameterInfo` elementu członkowskiego querydef dla określonej nazwy parametru lub indeksu do kolekcji Parameters. Można użyć funkcji elementu członkowskiego [CDaoQueryDef:::GetParameterCount](../../mfc/reference/cdaoquerydef-class.md#getparametercount) w połączeniu z `GetParameterInfo` do pętli za pośrednictwem parameters kolekcji.

Informacje pobierane przez funkcję elementu członkowskiego [CDaoQueryDef::GetParameterInfo](../../mfc/reference/cdaoquerydef-class.md#getparameterinfo) są przechowywane w `CDaoParameterInfo` strukturze. Wywołanie `GetParameterInfo` querydef obiektu, w którego parametrów kolekcji parametr obiektu jest przechowywany.

> [!NOTE]
> Jeśli chcesz uzyskać lub ustawić tylko wartość parametru, należy użyć funkcji członkowskich [GetParamValue](../../mfc/reference/cdaorecordset-class.md#getparamvalue) `CDaoRecordset`i [SetParamValue](../../mfc/reference/cdaorecordset-class.md#setparamvalue) klasy .

`CDaoParameterInfo`definiuje również `Dump` funkcję elementu członkowskiego w kompilacjach debugowania. Można użyć `Dump` do zrzutu `CDaoParameterInfo` zawartości obiektu.

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxdao.h

## <a name="see-also"></a>Zobacz też

[Struktury, style, wywołania zwrotne i mapy komunikatów](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[Klasa CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md)
