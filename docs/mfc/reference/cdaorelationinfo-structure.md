---
title: Cdaorelationinfo — struktura | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 06/25/2018
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
ms.openlocfilehash: 0fedf6ad90af670a462b0ccac23cc599a1a13e26
ms.sourcegitcommit: 6408139d5f5ff8928f056bde93d20eecb3520361
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/02/2018
ms.locfileid: "37336361"
---
# <a name="cdaorelationinfo-structure"></a>CDaoRelationInfo — Struktura
`CDaoRelationInfo` Struktura zawiera informacje dotyczące relacji zdefiniowanych między polami dwiema tabelami w [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) obiektu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
struct CDaoRelationInfo  
{  
    CDaoRelationInfo();                     // Constructor  
    CString m_strName;                      // Primary  
    CString m_strTable;                     // Primary  
    CString m_strForeignTable;              // Primary  
    long m_lAttributes;                     // Secondary  
    CDaoRelationFieldInfo* m_pFieldInfos;   // Secondary  
    short m_nFields;                        // Secondary
    // Below the // Implementation comment:
    // Destructor, not otherwise documented  
};  
```  
  
#### <a name="parameters"></a>Parametry  
*m_strName*  
 Unikatowej nazwy obiektu relacji. Aby uzyskać więcej informacji zobacz temat "Nazwa właściwości" w Pomocy programu DAO.  
  
 *m_strTable*  
 Nazwy tabeli podstawowej w relacji.  
  
 *m_strForeignTable*  
 Nazwy tabeli obcego w relacji. Obcy jest tabela zawiera klucze obce. Ogólnie rzecz biorąc obcego tabela służy do nawiązywania lub wymuszają więzy integralności. Obcy tabeli jest zazwyczaj na wielu stronach relacji jeden do wielu. Przykładami tabel obcych tabele zawierające kody stanów Ameryki ani kanadyjski prowincje zamówienia.  
  
 *m_lAttributes*  
 Zawiera informacje o typie relacji. Wartość tego elementu członkowskiego może być dowolny z następujących czynności:  
  
- `dbRelationUnique` Jest to relacja jeden do jednego.  
  
- `dbRelationDontEnforce` Relacja nie jest wymuszane (integralność referencyjna).  
  
- `dbRelationInherited` Relacja istnieje w bazie danych, innych niż bieżące, która zawiera dwie tabele dołączone.  
  
- `dbRelationLeft` Relacja jest lewego sprzężenia. Lewe sprzężenie zewnętrzne obejmuje wszystkie rekordy z pierwszego (po lewej stronie) z dwóch tabel, nawet w przypadku braku pasujących wartości w rekordach w drugiej tabeli (po prawej stronie).  
  
- `dbRelationRight` Relacja jest prawego sprzężenia. Prawe sprzężenie zewnętrzne obejmuje wszystkie rekordy z drugim (po prawej stronie) z dwóch tabel, nawet w przypadku braku pasujących wartości dla rekordów w pierwszej tabeli (po lewej stronie).  
  
- `dbRelationUpdateCascade` Aktualizacje będą narastać kaskadowo.  
  
- `dbRelationDeleteCascade` Kaskadowo zostaną usunięte.  
  
*m_pFieldInfos*  
 Wskaźnik do tablicy [cdaorelationfieldinfo —](../../mfc/reference/cdaorelationfieldinfo-structure.md) struktury. Tablica zawiera jeden obiekt dla każdego pola w relacji. `m_nFields` Element członkowski danych podaje liczbę elementów tablicy.  
  
*m_nfields —*  
 Liczba `CDaoRelationFieldInfo` obiekty w `m_pFieldInfos` element członkowski danych.  
  
## <a name="remarks"></a>Uwagi  
 Odwołania do podstawowym i pomocniczym powyżej wskazują, jak informacji jest zwróconych przez [GetRelationInfo](../../mfc/reference/cdaodatabase-class.md#getrelationinfo) funkcja elementu członkowskiego w klasie `CDaoDatabase`.  
  
 Obiekty relacji nie są reprezentowane przez klasę MFC. Zamiast tego, obiekt DAO MFC obiektu bazowego `CDaoDatabase` klasa przechowuje kolekcję obiektów relacji: `CDaoDatabase` dostarcza funkcji elementów członkowskich na dostęp do niektórych poszczególnych elementów informacji o relacji, lub można uzyskiwać do nich dostęp w całości z `CDaoRelationInfo` obiektu przez wywołanie metody `GetRelationInfo` funkcja elementu członkowskiego krawędzi zawierającego go obiektu bazy danych.  
  
 Informacje o pobrane przez [CDaoDatabase::GetRelationInfo](../../mfc/reference/cdaodatabase-class.md#getrelationinfo) funkcja członkowska jest przechowywany w `CDaoRelationInfo` struktury. `CDaoRelationInfo` definiuje również `Dump` kompilacje funkcja elementu członkowskiego podczas debugowania. Możesz użyć `Dump` do porzucenia zawartość `CDaoRelationInfo` obiektu.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxdao.h  
  
## <a name="see-also"></a>Zobacz też  
 [Struktura CDaoRelationFieldInfo](../../mfc/reference/cdaorelationfieldinfo-structure.md)
