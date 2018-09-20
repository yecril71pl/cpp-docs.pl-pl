---
title: Cdaorelationfieldinfo — struktura | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CDaoRelationFieldInfo
dev_langs:
- C++
helpviewer_keywords:
- DAO (Data Access Objects), Relations collection
- CDaoRelationFieldInfo structure [MFC]
ms.assetid: 47cb89ca-dc80-47ce-96fd-cc4b88512558
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0e61eb5a1abab68d4833bb8eb0953758234d9be6
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46423547"
---
# <a name="cdaorelationfieldinfo-structure"></a>CDaoRelationFieldInfo — Struktura

`CDaoRelationFieldInfo` Struktura zawiera informacje o polu w relacji zdefiniowanych dla obiektów dostępu do danych (DAO).

## <a name="syntax"></a>Składnia

```
struct CDaoRelationFieldInfo
{
    CString m_strName;           // Primary
    CString m_strForeignName;    // Primary
};
```

#### <a name="parameters"></a>Parametry

*m_strName*<br/>
Nazwa pola w tabeli podstawowej relacji.

*m_strForeignName*<br/>
Nazwa pola w tabeli obcego relacji.

## <a name="remarks"></a>Uwagi

Obiekt DAO relacji określa pola w tabeli podstawowej i pól w tabeli obcej, które definiują relację. Odwołania do głównej w powyższej definicji struktury wskazują, jak informacje są zwracane `m_pFieldInfos` członkiem [cdaorelationinfo —](../../mfc/reference/cdaorelationinfo-structure.md) można uzyskać przez wywołanie obiektu [GetRelationInfo](../../mfc/reference/cdaodatabase-class.md#getrelationinfo)funkcji składowej klasy typu `CDaoDatabase`.

Obiekty relacji i pola relacji nie są reprezentowane przez klasę MFC. Zamiast tego należy obiekt DAO obiektów podstawowych obiektów klasy MFC [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) zawiera kolekcję obiektów relacji o nazwie kolekcji relacji. Każdy obiekt relacji z kolei zawiera kolekcję obiektów pola relacji. Każdy obiekt pola relacji jest skorelowane pola w tabeli podstawowej za pomocą pola w tabeli obcego. Razem obiektów pola relacji definiują grupę pól w każdej tabeli, które razem definiują relacji. `CDaoDatabase` zapewnia dostęp do obiektów relacji z `CDaoRelationInfo` obiektu przez wywołanie metody `GetRelationInfo` funkcja elementu członkowskiego. `CDaoRelationInfo` Obiektu, to znaczy, ma składową danych `m_pFieldInfos`, który wskazuje na tablicę `CDaoRelationFieldInfo` obiektów.

Wywołaj [GetRelationInfo](../../mfc/reference/cdaodatabase-class.md#getrelationinfo) funkcji składowej typu zawierającego `CDaoDatabase` obiekt, w których relacje kolekcji jest przechowywany obiekt relacji Cię interesuje. Następnie uzyskać dostęp do `m_pFieldInfos` członkiem [cdaorelationinfo —](../../mfc/reference/cdaorelationinfo-structure.md) obiektu. `CDaoRelationFieldInfo` definiuje również `Dump` kompilacje funkcja elementu członkowskiego podczas debugowania. Możesz użyć `Dump` do porzucenia zawartość `CDaoRelationFieldInfo` obiektu.

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxdao.h

## <a name="see-also"></a>Zobacz też

[Struktury, style, wywołania zwrotne i mapy komunikatów](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[Struktura CDaoRelationInfo](../../mfc/reference/cdaorelationinfo-structure.md)
