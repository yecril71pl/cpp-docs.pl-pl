---
title: Klasa CMapStringToString | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMapStringToString
- AFXCOLL/CMapStringToString
- AFXCOLL/CMapStringToString::CPair
- AFXCOLL/CMapStringToOb::CMapStringToOb
- AFXCOLL/CMapStringToOb::GetCount
- AFXCOLL/CMapStringToOb::GetHashTableSize
- AFXCOLL/CMapStringToOb::GetNextAssoc
- AFXCOLL/CMapStringToOb::GetSize
- AFXCOLL/CMapStringToOb::GetStartPosition
- AFXCOLL/CMapStringToOb::HashKey
- AFXCOLL/CMapStringToOb::InitHashTable
- AFXCOLL/CMapStringToOb::IsEmpty
- AFXCOLL/CMapStringToOb::Lookup
- AFXCOLL/CMapStringToOb::LookupKey
- AFXCOLL/CMapStringToString::PGetFirstAssoc
- AFXCOLL/CMapStringToString::PGetNextAssoc
- AFXCOLL/CMapStringToString::PLookup
- AFXCOLL/CMapStringToOb::RemoveAll
- AFXCOLL/CMapStringToOb::RemoveKey
- AFXCOLL/CMapStringToOb::SetAt
dev_langs:
- C++
helpviewer_keywords:
- CMapStringToString [MFC], CPair
- CMapStringToOb [MFC], CMapStringToOb
- CMapStringToOb [MFC], GetCount
- CMapStringToOb [MFC], GetHashTableSize
- CMapStringToOb [MFC], GetNextAssoc
- CMapStringToOb [MFC], GetSize
- CMapStringToOb [MFC], GetStartPosition
- CMapStringToOb [MFC], HashKey
- CMapStringToOb [MFC], InitHashTable
- CMapStringToOb [MFC], IsEmpty
- CMapStringToOb [MFC], Lookup
- CMapStringToOb [MFC], LookupKey
- CMapStringToString [MFC], PGetFirstAssoc
- CMapStringToString [MFC], PGetNextAssoc
- CMapStringToString [MFC], PLookup
- CMapStringToOb [MFC], RemoveAll
- CMapStringToOb [MFC], RemoveKey
- CMapStringToOb [MFC], SetAt
ms.assetid: b45794c2-fe6b-4edb-a8ca-faa03b57b4a8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a196e2f3f4641d94bbbbda57dd1471066fb1dfa2
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="cmapstringtostring-class"></a>Klasa CMapStringToString
Obsługuje mapy `CString` obiektów, wyznaczaną przez `CString` obiektów.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CMapStringToString : public CObject  
```  
  
## <a name="members"></a>Elementy członkowskie  
 Funkcje Członkowskie `CMapStringToString` są podobne do funkcji Członkowskich klasy [CMapStringToOb](../../mfc/reference/cmapstringtoob-class.md). Ze względu na to podobieństwa, można użyć `CMapStringToOb` odwołania dokumentacji charakterystykę funkcja elementu członkowskiego. Po wyświetleniu `CObject` wskaźnik wartości zwracanej lub "output" parametru, funkcji zastępuje wskaźnik do `char`. Po wyświetleniu `CObject` wskaźnika jako parametr funkcji "wejściowy" zastępuje wskaźnik do `char`.  
  
 `BOOL CMapStringToOb::Lookup(const char*<key>, CObject*&<rValue>) const;`  
  
 na przykład umożliwia to  
  
 `BOOL CMapStringToString::Lookup(LPCTSTR<key>, CString&<rValue>) const;`  
  
### <a name="public-structures"></a>Publiczny struktury  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CMapStringToString::CPair](#cpair)|Zagnieżdżone struktury zawierające wartości klucza i wartość ciągu skojarzonego obiektu.|  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CMapStringToOb::CMapStringToOb](../../mfc/reference/cmapstringtoob-class.md#cmapstringtoob)|Konstruktor.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CMapStringToOb::GetCount](../../mfc/reference/cmapstringtoob-class.md#getcount)|Zwraca liczbę elementów na tej mapie.|  
|[CMapStringToOb::GetHashTableSize](../../mfc/reference/cmapstringtoob-class.md#gethashtablesize)|Określa bieżąca liczba elementów w tablicy skrótów.|  
|[CMapStringToOb::GetNextAssoc](../../mfc/reference/cmapstringtoob-class.md#getnextassoc)|Pobiera następnego elementu potrzeby iteracji.|  
|[CMapStringToOb::GetSize](../../mfc/reference/cmapstringtoob-class.md#getsize)|Zwraca liczbę elementów na tej mapie.|  
|[CMapStringToOb::GetStartPosition](../../mfc/reference/cmapstringtoob-class.md#getstartposition)|Zwraca pozycję pierwszego elementu.|  
|[CMapStringToOb::HashKey](../../mfc/reference/cmapstringtoob-class.md#hashkey)|Oblicza wartość skrótu z określonym kluczem.|  
|[CMapStringToOb::InitHashTable](../../mfc/reference/cmapstringtoob-class.md#inithashtable)|Inicjuje tablicy skrótów.|  
|[CMapStringToOb::IsEmpty](../../mfc/reference/cmapstringtoob-class.md#isempty)|Testy dla warunku pusta Mapa (Brak elementów).|  
|[CMapStringToOb::Lookup](../../mfc/reference/cmapstringtoob-class.md#lookup)|Wyszukuje void wskaźnik oparte na kluczu wskaźnika typu void. Wartość wskaźnika, nie jednostki, który wskazuje, służy do porównywania klucza.|  
|[CMapStringToOb::LookupKey](../../mfc/reference/cmapstringtoob-class.md#lookupkey)|Zwraca odwołanie do klucz skojarzony z określoną wartością klucza.|  
|[CMapStringToString::PGetFirstAssoc](#pgetfirstassoc)|Pobiera wskaźnik do pierwszego `CString` na mapie.|  
|[CMapStringToString::PGetNextAssoc](#pgetnextassoc)|Pobiera wskaźnik do następnego `CString` potrzeby iteracji.|  
|[CMapStringToString::PLookup](#plookup)|Zwraca wskaźnik do `CString` którego wartość odpowiada określonej wartości.|  
|[CMapStringToOb::RemoveAll](../../mfc/reference/cmapstringtoob-class.md#removeall)|Usuwa wszystkie elementy z tej mapy.|  
|[CMapStringToOb::RemoveKey](../../mfc/reference/cmapstringtoob-class.md#removekey)|Usuwa element określony przez klucz.|  
|[CMapStringToOb::SetAt](../../mfc/reference/cmapstringtoob-class.md#setat)|Wstawia element do mapy; zastępuje istniejący element, jeśli dopasowany klucz zostanie znaleziony.|  
  
### <a name="public-operators"></a>Operatory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[[CMapStringToOb::operator]](../../mfc/reference/cmapstringtoob-class.md#operator_at)|Wstawia element do mapy — operator podstawienia dla `SetAt`.|  
  
## <a name="remarks"></a>Uwagi  
 `CMapStringToString` zawiera `IMPLEMENT_SERIAL` makro do obsługi serializacji i zrzucanie swoich elementów. Każdy element jest serializowany z kolei jeśli mapy jest przechowywany w archiwum, za pomocą przeciążenia wstawiania ( **<<**) — operator lub `Serialize` funkcję elementu członkowskiego.  
  
 Jeśli potrzebujesz zrzutu osoba `CString` -  `CString` elementów, musisz ustawić głębokość kontekstu zrzutu 1 lub większą.  
  
 Gdy `CMapStringToString` obiekt jest usunięty lub gdy jego elementy są usuwane, `CString` obiekty są usuwane odpowiednio.  
  
 Aby uzyskać więcej informacji na temat `CMapStringToString`, zapoznaj się z artykułem [kolekcji](../../mfc/collections.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CMapStringToString`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxcoll.h  
  
##  <a name="cpair"></a>  CMapStringToString::CPair  
 Zawiera wartość klucza i wartość ciągu skojarzonego obiektu.  
  
### <a name="remarks"></a>Uwagi  
 To jest strukturą zagnieżdżone w obrębie klasy [CMapStringToString](../../mfc/reference/cmapstringtostring-class.md).  
  
 Struktura składa się z dwóch pól:  
  
- **klucz** rzeczywistej wartości Typ klucza.  
  
- **wartość** wartość skojarzonego obiektu.  
  
 Jest on używany do przechowywania wartości zwracanych z [CMapStringToString::PLookup](#plookup), [CMapStringToString::PGetFirstAssoc](#pgetfirstassoc), i [CMapStringToString::PGetNextAssoc](#pgetnextassoc).  
  
### <a name="example"></a>Przykład  
  Przykład użycia, zobacz przykład [CMapStringToString::PLookup](#plookup).  
  
##  <a name="pgetfirstassoc"></a>  CMapStringToString::PGetFirstAssoc  
 Zwraca pierwszy wpis obiektu mapy.  
  
```  
const CPair* PGetFirstAssoc() const;

CPair* PGetFirstAssoc();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do pierwszego wpis w mapie; zobacz [CMapStringToString::CPair](#cpair). Jeśli tablica jest pusta, wartość jest `NULL`.  
  
### <a name="remarks"></a>Uwagi  
 Wywołanie tej funkcji, aby zwracać wskaźnik pierwszego elementu w obiekcie mapy.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCCollections#73](../../mfc/codesnippet/cpp/cmapstringtostring-class_1.cpp)]  
  
##  <a name="pgetnextassoc"></a>  CMapStringToString::PGetNextAssoc  
 Pobiera element map wskazywana przez `pAssocRec`.  
  
```  
const CPair *PGetNextAssoc(const CPair* pAssoc) const;  
  
CPair *PGetNextAssoc(const CPair* pAssoc);
```  
  
### <a name="parameters"></a>Parametry  
 *pAssoc*  
 Wskazuje wpis mapy zwrócony przez poprzednie [PGetNextAssoc](#pgetnextassoc) lub [PGetFirstAssoc](#pgetfirstassoc) wywołania.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do następnego wpisu w mapowaniu; zobacz [CMapStringToString::CPair](#cpair). Jeśli element jest ostatni w planie, wartość jest **NULL**.  
  
### <a name="remarks"></a>Uwagi  
 Wywołaj tę metodę, aby wykonać iterację wszystkie elementy na mapie. Pierwszy element z wywołaniem do pobrania `PGetFirstAssoc` , a następnie wykonać iterację mapy kolejne wywołania `PGetNextAssoc`.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CMapStringToString::PGetFirstAssoc](#pgetfirstassoc).  
  
##  <a name="plookup"></a>  CMapStringToString::PLookup  
 Wyszukuje wartość mapowane na danym kluczem.  
  
```  
const CPair* PLookup(LPCTSTR key) const;

CPair* PLookup(LPCTSTR key);
```  
  
### <a name="parameters"></a>Parametry  
 `key`  
 Wskaźnik do klucza dla elementu, który ma zostać wyszukany.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do określonego klucza.  
  
### <a name="remarks"></a>Uwagi  
 Wywołaj tę metodę, aby wyszukać map element, za pomocą klucza, która dokładnie odpowiada danym kluczem.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCCollections#74](../../mfc/codesnippet/cpp/cmapstringtostring-class_2.cpp)]  
  
## <a name="see-also"></a>Zobacz też  
 [Przykładowe MFC ZBIERANIE](../../visual-cpp-samples.md)   
 [CObject — klasa](../../mfc/reference/cobject-class.md)   
 [Wykres hierarchii](../../mfc/hierarchy-chart.md)



