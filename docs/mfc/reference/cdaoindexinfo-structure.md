---
title: Cdaoindexinfo — struktura | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CDaoIndexInfo
dev_langs:
- C++
helpviewer_keywords:
- DAO (Data Access Objects), Indexes collection
- CDaoIndexInfo structure [MFC]
ms.assetid: 251d8285-78ce-4716-a0b3-ccc3395fc437
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3d8c98181a9ec049308d7b85e57c028740927cc2
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="cdaoindexinfo-structure"></a>CDaoIndexInfo — Struktura
`CDaoIndexInfo` Struktury zawiera informacje o obiekcie indeksu zdefiniowany dla obiektów dostępu do danych (DAO).  
  
## <a name="syntax"></a>Składnia  
  
```  
struct CDaoIndexInfo {  
    CDaoIndexInfo();
*// Constructor  
    CString m_strName;  // Primary  
    CDaoIndexFieldInfo* m_pFieldInfos;  // Primary  
    short m_nFields;    // Primary  
    BOOL m_bPrimary;    // Secondary  
    BOOL m_bUnique;     // Secondary  
    BOOL m_bClustered;  // Secondary  
    BOOL m_bIgnoreNulls;                // Secondary  
    BOOL m_bRequired;   // Secondary  
    BOOL m_bForeign;    // Secondary  
    long m_lDistinctCount;              // All  
 *// Below the // Implementation comment: *// Destructor, not otherwise documented  
};   
```  
  
#### <a name="parameters"></a>Parametry  
 `m_strName`  
 Unikatowej nazwy obiektu pola. Aby uzyskać więcej informacji zobacz temat "Właściwości Name" w pomocy DAO.  
  
 `m_pFieldInfos`  
 Wskaźnik do tablicy [cdaoindexfieldinfo —](../../mfc/reference/cdaoindexfieldinfo-structure.md) obiektów wskazujące, które pola tabledef lub zestawu rekordów pola klucza w indeksie. Każdy obiekt identyfikuje jedno pole w indeksie. Rosnąca domyślnej kolejności indeksu. Obiekt indeksu może mieć co najmniej jedno pole reprezentujący kluczy indeksu dla każdego rekordu. Mogą one rosnącej, malejącej, lub połączenie.  
  
 `m_nFields`  
 Liczba pól przechowywane w `m_pFieldInfos`.  
  
 *m_bPrimary*  
 W przypadku właściwości podstawowego **TRUE**, obiekt indeksu reprezentuje podstawowy indeks. Podstawowy indeks składa się z co najmniej jedno pole, które jednoznacznie identyfikują wszystkie rekordy w tabeli w preferowanej kolejności. Ponieważ pole indeksu musi być unikatowa, również ma ustawioną właściwość unikatowy indeks obiektu **TRUE** w DAO. Jeśli podstawowy indeks obejmuje więcej niż jedno pole, każde pole może zawierać zduplikowanych wartości, ale każda kombinacja wartości od indeksowanego pól muszą być unikatowe. Podstawowy indeks składa się z klucza tabeli i zwykle zawiera te same pola jako klucz podstawowy.  
  
 Po ustawieniu klucza podstawowego dla tabeli jako podstawowego indeksu tabeli jest automatycznie zdefiniowany klucz podstawowy. Aby uzyskać więcej informacji zobacz tematy "Właściwości podstawowego" i "Właściwości Unique" w pomocy DAO.  
  
> [!NOTE]
>  Może istnieć, co najwyżej jeden indeks podstawowy w tabeli.  
  
 *m_bUnique*  
 Wskazuje, czy obiekt indeksu reprezentuje unikatowego indeksu dla tabeli. Jeśli ta właściwość jest **TRUE**, obiekt indeksu reprezentuje indeks, która jest unikatowa. Unikatowy indeks składa się z jednego lub więcej pól, które logicznie Rozmieść wszystkie rekordy w tabeli w kolejności unikatowy, wstępnie zdefiniowane. Jeśli indeks obejmuje co najmniej dwa pola, wartości w tym polu musi być unikatowa dla całej tabeli. Jeśli indeks obejmuje więcej niż jedno pole, każde pole może zawierać zduplikowanych wartości, ale każda kombinacja wartości od indeksowanego pól muszą być unikatowe.  
  
 Jeśli ustawiono właściwości obiektu indeksu Unique i podstawowej **TRUE**, indeks jest unikatowy i podstawowego: unikatowo identyfikuje wszystkie rekordy w tabeli w kolejności wstępnie zdefiniowane, logiczną. Jeśli ustawiono właściwość głównej **FALSE**, indeks jest pomocniczy indeks. Indeksów pomocniczych (klucza i nonkey) logicznie Rozmieść rekordów w preferowanej kolejności bez służy jako identyfikator rekordów w tabeli.  
  
 Aby uzyskać więcej informacji zobacz tematy "Właściwości podstawowego" i "Właściwości Unique" w pomocy DAO.  
  
 *m_bClustered*  
 Wskazuje, czy obiekt indeksu reprezentuje indeksu klastrowanego dla tabeli. Jeśli ta właściwość jest **TRUE**, obiekt indeksu reprezentuje indeks klastrowany; w przeciwnym razie nie. Indeks klastrowany zawiera jeden lub więcej nonkey pól, razem Rozmieść wszystkie rekordy w tabeli w preferowanej kolejności. Dane w tabeli z indeksem klastrowanym dosłownie znajduje się w kolejności określonej przez indeks klastrowany. Indeks klastrowany zapewnia wydajny dostęp do rekordów w tabeli. Aby uzyskać więcej informacji zobacz temat "W klastrze Property" w pomocy DAO.  
  
> [!NOTE]
>  Właściwości klastra jest ignorowany dla baz danych używających aparat bazy danych programu Microsoft Jet, ponieważ aparat bazy danych Jet nie obsługuje indeksy klastrowane.  
  
 *m_bIgnoreNulls*  
 Wskazuje, czy pozycje indeksu dla rekordów, które mają wartości Null w swoich pól indeksu. Jeśli ta właściwość jest **TRUE**, pól o wartości Null nie ma pozycji indeksu. Aby wyszukiwanie rekordów za pomocą pola szybciej, można określić indeksu dla pola. Jeśli Zezwalaj wpisy wartości Null w indeksowanym polu i oczekują wiele wpisów na wartość Null, można ustawić właściwości IgnoreNulls dla obiekt indeksu **TRUE** Aby zmniejszyć ilość miejsca do magazynowania, która używa indeksu. Ustawienie właściwości IgnoreNulls i ustawienie właściwości wymagane wspólnie określają, czy rekordu o wartości Null indeks ma wpis indeksu, jak to pokazano w poniższej tabeli.  
  
|IgnoreNulls|Wymagane|W polu Indeks o wartości null|  
|-----------------|--------------|-------------------------|  
|True|False|Wartości null są dozwolone; nie dodano wpis indeksu.|  
|False|False|Wartości null są dozwolone; dodaje wpis indeksu.|  
|Wartość PRAWDA lub FAŁSZ|True|Wartość null nie jest dozwolona; nie dodano wpis indeksu.|  
  
 Aby uzyskać więcej informacji zobacz temat "IgnoreNulls Property" w pomocy DAO.  
  
 `m_bRequired`  
 Wskazuje, czy obiekt DAO indeksu wymaga wartości innej niż Null. Jeśli ta właściwość jest **TRUE**, obiekt indeks nie zezwala na wartości Null. Aby uzyskać więcej informacji zobacz temat "Wymagana właściwość" w pomocy DAO.  
  
> [!TIP]
>  Po ustawieniu tej właściwości dla obiekt DAO indeksu lub obiektu pola (zawarty w tabledef, rekordów lub obiektu querydef), należy ustawić go dla obiekt pola. Ważność ustawienie właściwości dla obiektu pola zaznaczono przed obiekt indeksu.  
  
 *m_bForeign*  
 Wskazuje, czy obiekt indeksu reprezentuje klucza obcego w tabeli. Jeśli ta właściwość jest **TRUE**, indeks reprezentuje klucza obcego w tabeli. Klucz obcy składa się z co najmniej jedno pole obcy tabeli, które jednoznacznie identyfikują wiersze w tabeli podstawowej. Aparat bazy danych programu Microsoft Jet tworzy obiekt indeksu dla tabeli obcego i ustawia właściwość obcego podczas tworzenia relacji, która wymusza integralności referencyjnej. Aby uzyskać więcej informacji zobacz temat "Obcego Property" w pomocy DAO.  
  
 *m_lDistinctCount*  
 Wskazuje liczbę unikatowych wartości dla obiekt indeksu, uwzględnionych w skojarzonej tabeli. Sprawdź właściwość DistinctCount, aby określić liczbę unikatowych wartości lub kluczy w indeksie. Dowolny klawisz, zalicza się tylko raz, mimo że może istnieć wiele wystąpień tej wartości indeksu pozwala na zduplikowane wartości. Informacje te są przydatne w aplikacjach, które podejmować pod kątem dostępu do danych przez dotyczące indeksu. Liczba unikatowych wartości jest nazywana Kardynalność indeksu obiektu. Właściwość DistinctCount nie będzie zawsze odzwierciedlają rzeczywista liczba kluczy w określonym czasie. Na przykład zmiany spowodowane wycofywania transakcji nie zostaną odzwierciedlone natychmiast we właściwości DistinctCount. Aby uzyskać więcej informacji zobacz temat "DistinctCount Property" w pomocy DAO.  
  
## <a name="remarks"></a>Uwagi  
 Odwołania do podstawowej, pomocniczej i wszystkie powyższe wskazują, jak informacje zwracane przez `GetIndexInfo` funkcji Członkowskich w klasach [CDaoTableDef](../../mfc/reference/cdaotabledef-class.md#getindexinfo) i [cdaorecordset —](../../mfc/reference/cdaorecordset-class.md#getindexinfo).  
  
 Indeks obiekty nie są reprezentowane przez klasę MFC. Zamiast tego DAO obiektów MFC obiektów klasy [CDaoTableDef](../../mfc/reference/cdaotabledef-class.md) lub [cdaorecordset —](../../mfc/reference/cdaorecordset-class.md) zawiera kolekcję obiektów indeksu, nazywanych kolekcji indeksów. Te klasy podać funkcji elementów członkowskich, aby uzyskiwać dostęp do poszczególnych elementów informacji indeksu lub uzyskać dostępu do nich jednocześnie z `CDaoIndexInfo` obiektu przez wywołanie metody `GetIndexInfo` funkcji członkowskiej krawędzi zawierającego go obiektu.  
  
 `CDaoIndexInfo` Konstruktor i destruktor, aby można było poprawnie przydzielić i cofnięcia przydzielenia pola informacji o indeksie `m_pFieldInfos`.  
  
 Informacje o pobrane przez `GetIndexInfo` funkcji członkowskiej klasy obiektu tabledef są przechowywane w `CDaoIndexInfo` struktury. Wywołanie `GetIndexInfo` funkcji członkowskiej klasy obiektu zawierającego tabledef, w których kolekcji indeksów jest obiekt indeksu. `CDaoIndexInfo` definiuje również `Dump` kompilacje funkcji członkowskiej podczas debugowania. Można użyć `Dump` do zrzutu zawartość `CDaoIndexInfo` obiektu.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxdao.h  
  
## <a name="see-also"></a>Zobacz też  
 [Struktury, style, wywołania zwrotne i mapy komunikatów](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CDaoTableDef::GetIndexInfo](../../mfc/reference/cdaotabledef-class.md#getindexinfo)

