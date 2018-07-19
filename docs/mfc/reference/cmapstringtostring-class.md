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
ms.openlocfilehash: 613e49478349779709571927ee38b0903f141730
ms.sourcegitcommit: 6408139d5f5ff8928f056bde93d20eecb3520361
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/02/2018
ms.locfileid: "37336244"
---
# <a name="cmapstringtostring-class"></a>Klasa CMapStringToString
Obsługuje mapy `CString` obiektów kluczach `CString` obiektów.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CMapStringToString : public CObject  
```  
  
## <a name="members"></a>Elementy członkowskie  
 Funkcje elementów członkowskich `CMapStringToString` są podobne do funkcji elementów członkowskich klasy [CMapStringToOb](../../mfc/reference/cmapstringtoob-class.md). Ze względu na to podobieństwa można użyć `CMapStringToOb` dokumentacji kątem specyfiki funkcja elementu członkowskiego. Po wyświetleniu `CObject` wskaźnika jako wartość zwracaną lub "output" funkcji parametr, Zastąp wskaźnik do **char**. Po wyświetleniu `CObject` wskaźnika jako parametr funkcji "danych wejściowych" Zastąp wskaźnik do **char**.  
  
 `BOOL CMapStringToOb::Lookup(const char*<key>, CObject*&<rValue>) const;`  
  
 na przykład przekłada się na  
  
 `BOOL CMapStringToString::Lookup(LPCTSTR<key>, CString&<rValue>) const;`  
  
### <a name="public-structures"></a>Publiczne struktury  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CMapStringToString::CPair](#cpair)|Struktura zagnieżdżona zawierające wartości klucza i wartości z obiektem ciągu skojarzone.|  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CMapStringToOb::CMapStringToOb](../../mfc/reference/cmapstringtoob-class.md#cmapstringtoob)|Konstruktor.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CMapStringToOb::GetCount](../../mfc/reference/cmapstringtoob-class.md#getcount)|Zwraca liczbę elementów na tej mapie.|  
|[CMapStringToOb::GetHashTableSize](../../mfc/reference/cmapstringtoob-class.md#gethashtablesize)|Określa aktualną liczbę elementów w tabeli wyznaczania wartości skrótu.|  
|[CMapStringToOb::GetNextAssoc](../../mfc/reference/cmapstringtoob-class.md#getnextassoc)|Pobiera następny element do wykonania iteracji.|  
|[CMapStringToOb::GetSize](../../mfc/reference/cmapstringtoob-class.md#getsize)|Zwraca liczbę elementów na tej mapie.|  
|[CMapStringToOb::GetStartPosition](../../mfc/reference/cmapstringtoob-class.md#getstartposition)|Zwraca pozycję pierwszego elementu.|  
|[CMapStringToOb::HashKey](../../mfc/reference/cmapstringtoob-class.md#hashkey)|Oblicza wartość skrótu dla określonego klucza.|  
|[CMapStringToOb::InitHashTable](../../mfc/reference/cmapstringtoob-class.md#inithashtable)|Inicjuje tabelę mieszania.|  
|[CMapStringToOb::IsEmpty](../../mfc/reference/cmapstringtoob-class.md#isempty)|Testuje pod kątem warunku pusta Mapa (Brak elementów).|  
|[CMapStringToOb::Lookup](../../mfc/reference/cmapstringtoob-class.md#lookup)|Wyszukuje wskaźnika void oparte na kluczu wskaźnika void. Wartość wskaźnika, a nie jednostki, który wskazuje, służy do porównywania kluczy.|  
|[CMapStringToOb::LookupKey](../../mfc/reference/cmapstringtoob-class.md#lookupkey)|Zwraca odwołanie do klucz skojarzony z określoną wartością klucza.|  
|[CMapStringToString::PGetFirstAssoc](#pgetfirstassoc)|Pobiera wskaźnik do pierwszego `CString` na mapie.|  
|[CMapStringToString::PGetNextAssoc](#pgetnextassoc)|Pobiera wskaźnik do następnego `CString` do wykonania iteracji.|  
|[CMapStringToString::PLookup](#plookup)|Zwraca wskaźnik do `CString` którego wartość odpowiada określonej wartości.|  
|[CMapStringToOb::RemoveAll](../../mfc/reference/cmapstringtoob-class.md#removeall)|Usuwa wszystkie elementy z tej mapie.|  
|[CMapStringToOb::RemoveKey](../../mfc/reference/cmapstringtoob-class.md#removekey)|Usuwa element określony przez klucz.|  
|[CMapStringToOb::SetAt](../../mfc/reference/cmapstringtoob-class.md#setat)|Wstawia element do mapy; zastępuje istniejący element, jeśli dopasowany klucz zostanie znaleziony.|  
  
### <a name="public-operators"></a>Operatory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[[] CMapStringToOb::operator](../../mfc/reference/cmapstringtoob-class.md#operator_at)|Wstawia element do mapy — operator podstawienia dla `SetAt`.|  
  
## <a name="remarks"></a>Uwagi  
 `CMapStringToString` dołącza `IMPLEMENT_SERIAL` makra do obsługi serializacji i zrzucanie z jego elementów. Każdy element jest serializowana z kolei Jeśli mapa jest przechowywany do archiwum, przy użyciu przeciążonych wstawiania ( **<<**) — operator lub `Serialize` funkcja elementu członkowskiego.  
  
 Jeśli potrzebujesz zrzutu indywidualnego `CString` -  `CString` elementów, należy ustawić głębokość kontekstu zrzutu 1 lub większą.  
  
 Gdy `CMapStringToString` obiekt zostanie usunięty lub gdy jego elementy są usuwane, `CString` obiekty są usuwane odpowiednio.  
  
 Aby uzyskać więcej informacji na temat `CMapStringToString`, zapoznaj się z artykułem [kolekcje](../../mfc/collections.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CMapStringToString`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxcoll.h  
  
##  <a name="cpair"></a>  CMapStringToString::CPair  
 Zawiera wartość klucza i wartości z obiektem ciągu skojarzone.  
  
### <a name="remarks"></a>Uwagi  
 Jest to struktura zagnieżdżona w klasie [CMapStringToString](../../mfc/reference/cmapstringtostring-class.md).  
  
 Struktura składa się z dwóch pól:  
  
- `key` Wartość rzeczywista typ klucza.  
  
- `value` Wartość skojarzonego obiektu.  
  
 Jest on używany do przechowywania wartości zwracanych z [CMapStringToString::PLookup](#plookup), [CMapStringToString::PGetFirstAssoc](#pgetfirstassoc), i [CMapStringToString::PGetNextAssoc](#pgetnextassoc).  
  
### <a name="example"></a>Przykład  
  Na przykład użycia, zobacz przykład [CMapStringToString::PLookup](#plookup).  
  
##  <a name="pgetfirstassoc"></a>  CMapStringToString::PGetFirstAssoc  
 Zwraca pierwszy wpis obiektu mapy.  
  
```  
const CPair* PGetFirstAssoc() const;

CPair* PGetFirstAssoc();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do pierwszej pozycji w mapowaniu; zobacz [CMapStringToString::CPair](#cpair). Jeśli mapa jest pusta, wartość jest równa NULL.  
  
### <a name="remarks"></a>Uwagi  
 Wywołaj tę funkcję, aby zwrócić wskaźnik do pierwszego elementu w obiektu mapy.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCCollections#73](../../mfc/codesnippet/cpp/cmapstringtostring-class_1.cpp)]  
  
##  <a name="pgetnextassoc"></a>  CMapStringToString::PGetNextAssoc  
 Pobiera element mapy, wskazane przez *pAssocRec*.  
  
```  
const CPair *PGetNextAssoc(const CPair* pAssoc) const;  
  
CPair *PGetNextAssoc(const CPair* pAssoc);
```  
  
### <a name="parameters"></a>Parametry  
 *pAssoc*  
 Wskazuje na wpis mapy zwrócony przez poprzednie [PGetNextAssoc](#pgetnextassoc) lub [PGetFirstAssoc](#pgetfirstassoc) wywołania.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do następnego wpisu w mapowaniu; zobacz [CMapStringToString::CPair](#cpair). Jeśli element jest ostatni w mapie, wartość jest wartością NULL.  
  
### <a name="remarks"></a>Uwagi  
 Wywołaj tę metodę do iteracji wszystkich elementów w mapie. Pobrać pierwszy element z wywołaniem `PGetFirstAssoc` i następnie iterację mapy za pomocą kolejne wywołania `PGetNextAssoc`.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CMapStringToString::PGetFirstAssoc](#pgetfirstassoc).  
  
##  <a name="plookup"></a>  CMapStringToString::PLookup  
 Wyszukuje wartość mapowane do danego klucza.  
  
```  
const CPair* PLookup(LPCTSTR key) const;

CPair* PLookup(LPCTSTR key);
```  
  
### <a name="parameters"></a>Parametry  
 *Klucz*  
 Wskaźnik do klucza dla elementu, który ma zostać wyszukany.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do określonego klucza.  
  
### <a name="remarks"></a>Uwagi  
 Wywołaj tę metodę, aby wyszukać element mapy za pomocą klucza, który dokładnie pasuje do danego klucza.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCCollections#74](../../mfc/codesnippet/cpp/cmapstringtostring-class_2.cpp)]  
  
## <a name="see-also"></a>Zobacz też  
 [Próbki MFC ZBIERANIE](../../visual-cpp-samples.md)   
 [Klasa CObject](../../mfc/reference/cobject-class.md)   
 [Wykres hierarchii](../../mfc/hierarchy-chart.md)



