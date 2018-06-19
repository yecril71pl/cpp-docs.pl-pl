---
title: Cdaorelationinfo — struktura | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CDaoRelationInfo
dev_langs:
- C++
helpviewer_keywords:
- DAO (Data Access Objects), Relations collection
- CDaoRelationInfo structure [MFC]
ms.assetid: 92dda090-fe72-4090-84ec-429498a48aad
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 112af640d020dc579c1ec2b1b7eace509daa451e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33366265"
---
# <a name="cdaorelationinfo-structure"></a>CDaoRelationInfo — Struktura
`CDaoRelationInfo` Struktura zawiera informacje dotyczące relacji między polami dwiema tabelami w [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) obiektu.  
  
## <a name="syntax"></a>Składnia  
  
```  
struct CDaoRelationInfo  
{  
    CDaoRelationInfo();
*// Constructor  
    CString m_strName;      // Primary  
    CString m_strTable;     // Primary  
    CString m_strForeignTable;              // Primary  
    long m_lAttributes;     // Secondary  
    CDaoRelationFieldInfo* m_pFieldInfos;   // Secondary  
    short m_nFields;        // Secondary *// Below the // Implementation comment: *// Destructor, not otherwise documented  
};  
```  
  
#### <a name="parameters"></a>Parametry  
 `m_strName`  
 Unikatowej nazwy obiektu relacji. Aby uzyskać więcej informacji zobacz temat "Właściwości Name" w pomocy DAO.  
  
 *m_strTable*  
 Nazwa tabeli podstawowej w relacji.  
  
 *m_strForeignTable*  
 Nazwa tabeli obcego w relacji. Obcy tabeli znajduje się tabela zawiera klucze obce. Ogólnie rzecz biorąc obcego tabela służy do nawiązywania lub wymusić integralności referencyjnej. Obcy tabeli jest zwykle po stronie "wielu" relacji jeden do wielu. Przykładami tabel obcych tabel zawierających kody stanów Ameryki ani prowincjach Kanady zamówień klienta.  
  
 `m_lAttributes`  
 Zawiera informacje o typie relacji. Wartość tego elementu może być jedną z następujących czynności:  
  
- **dbRelationUnique** jest relacja jeden do jednego.  
  
- **dbRelationDontEnforce** relacji nie jest wymuszana (nie integralności referencyjnej).  
  
- **dbRelationInherited** relacja istnieje w bazie danych innych niż bieżące zawiera dwie tabele dołączone.  
  
- **dbRelationLeft** relacji jest lewego sprzężenia. Lewe sprzężenie zewnętrzne zawiera wszystkie rekordy z pierwszej (lewa) z dwóch tabel, nawet jeśli nie ma pasujących wartości dla rekordów w drugiej tabeli (po prawej stronie).  
  
- **dbRelationRight** relacji jest prawo sprzężenia. Prawe sprzężenie zewnętrzne zawiera wszystkie rekordy z drugim (po prawej stronie) z dwóch tabel, nawet jeśli nie pasujących wartości dla rekordów w pierwszej tabeli (po lewej stronie).  
  
- **dbRelationUpdateCascade** aktualizacji będzie kaskadowo.  
  
- **dbRelationDeleteCascade** kaskadowo zostaną usunięte.  
  
 `m_pFieldInfos`  
 Wskaźnik do tablicy [cdaorelationfieldinfo —](../../mfc/reference/cdaorelationfieldinfo-structure.md) struktury. Tablica zawiera jeden obiekt dla każdego pola w relacji. `m_nFields` Element członkowski danych zawiera liczbę elementów tablicy.  
  
 `m_nFields`  
 Liczba `CDaoRelationFieldInfo` obiekty w `m_pFieldInfos` element członkowski danych.  
  
## <a name="remarks"></a>Uwagi  
 Odwołania do podstawowego i zapasowego powyżej wskazują, jak informacje zwracane przez [GetRelationInfo](../../mfc/reference/cdaodatabase-class.md#getrelationinfo) funkcji członkowskiej klasy `CDaoDatabase`.  
  
 Obiekty relacji nie są reprezentowane przez klasę MFC. Zamiast tego, obiekt DAO MFC obiektu podstawowego `CDaoDatabase` klasa obsługuje kolekcję obiektów relacji: `CDaoDatabase` funkcje Członkowskie dostaw na dostęp do niektórych poszczególnych elementów informacji o relacji, lub można uzyskiwać do nich dostęp w całości z `CDaoRelationInfo` obiektu przez wywołanie metody `GetRelationInfo` funkcji członkowskiej krawędzi zawierającego go obiektu bazy danych.  
  
 Informacje o pobrane przez [CDaoDatabase::GetRelationInfo](../../mfc/reference/cdaodatabase-class.md#getrelationinfo) funkcja członkowska jest przechowywany w `CDaoRelationInfo` struktury. `CDaoRelationInfo` definiuje również `Dump` kompilacje funkcji członkowskiej podczas debugowania. Można użyć `Dump` do zrzutu zawartość `CDaoRelationInfo` obiektu.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxdao.h  
  
## <a name="see-also"></a>Zobacz też  
 [Struktura CDaoRelationFieldInfo](../../mfc/reference/cdaorelationfieldinfo-structure.md)
