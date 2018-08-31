---
title: Klasa CMapStringToOb | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMapStringToOb
- AFXCOLL/CMapStringToOb
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
- AFXCOLL/CMapStringToOb::RemoveAll
- AFXCOLL/CMapStringToOb::RemoveKey
- AFXCOLL/CMapStringToOb::SetAt
dev_langs:
- C++
helpviewer_keywords:
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
- CMapStringToOb [MFC], RemoveAll
- CMapStringToOb [MFC], RemoveKey
- CMapStringToOb [MFC], SetAt
ms.assetid: 09653980-b885-4f3a-8594-0aeb7f94c601
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a6eea9b6005498c6c42017731db7ea706af96726
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43216993"
---
# <a name="cmapstringtoob-class"></a>Klasa CMapStringToOb
Klasa kolekcji słownika, która mapuje unikatowe `CString` obiekty do `CObject` wskaźników.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CMapStringToOb : public CObject  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CMapStringToOb::CMapStringToOb](#cmapstringtoob)|Konstruktor.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CMapStringToOb::GetCount](#getcount)|Zwraca liczbę elementów na tej mapie.|  
|[CMapStringToOb::GetHashTableSize](#gethashtablesize)|Określa aktualną liczbę elementów w tabeli wyznaczania wartości skrótu.|  
|[CMapStringToOb::GetNextAssoc](#getnextassoc)|Pobiera następny element do wykonania iteracji.|  
|[CMapStringToOb::GetSize](#getsize)|Zwraca liczbę elementów na tej mapie.|  
|[CMapStringToOb::GetStartPosition](#getstartposition)|Zwraca pozycję pierwszego elementu.|  
|[CMapStringToOb::HashKey](#hashkey)|Oblicza wartość skrótu dla określonego klucza.|  
|[CMapStringToOb::InitHashTable](#inithashtable)|Inicjuje tabelę mieszania.|  
|[CMapStringToOb::IsEmpty](#isempty)|Testuje pod kątem warunku pusta Mapa (Brak elementów).|  
|[CMapStringToOb::Lookup](#lookup)|Wyszukuje wskaźnika void oparte na kluczu wskaźnika void. Wartość wskaźnika, a nie jednostki, który wskazuje, służy do porównywania kluczy.|  
|[CMapStringToOb::LookupKey](#lookupkey)|Zwraca odwołanie do klucz skojarzony z określoną wartością klucza.|  
|[CMapStringToOb::RemoveAll](#removeall)|Usuwa wszystkie elementy z tej mapie.|  
|[CMapStringToOb::RemoveKey](#removekey)|Usuwa element określony przez klucz.|  
|[CMapStringToOb::SetAt](#setat)|Wstawia element do mapy; zastępuje istniejący element, jeśli dopasowany klucz zostanie znaleziony.|  
  
### <a name="public-operators"></a>Operatory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[[] CMapStringToOb::operator](#operator_at)|Wstawia element do mapy — operator podstawienia dla `SetAt`.|  
  
## <a name="remarks"></a>Uwagi  
 Po wstawieniu `CString` -  `CObject*` pary (element) do mapy, mogą efektywnie pobierania i usuwania pary za pomocą ciągu lub `CString` wartość jako klucz. Można również wykonać iterację przez wszystkie elementy na mapie.  
  
 Zmienna typu pozycja jest używane do dostępu alternatywnego wpis w wszystkie odmiany mapy. Można użyć pozycji, wpis "pamiętać" i do iteracji na mapie. Może się wydawać, sekwencyjnych według wartości kluczy; to tej iteracji nie jest dostępne. Sekwencja elementów pobrane jest nieokreślony.  
  
 `CMapStringToOb` dołącza `IMPLEMENT_SERIAL` makra do obsługi serializacji i zrzucanie z jego elementów. Każdy element jest serializowana z kolei Jeśli mapa jest przechowywany do archiwum, przy użyciu przeciążonych wstawiania ( **<<**) — operator lub `Serialize` funkcja elementu członkowskiego.  
  
 Jeśli potrzebujesz diagnostycznych zrzut poszczególnych elementów w mapie ( `CString` wartość i `CObject` zawartość), należy ustawić głębokość kontekstu zrzutu 1 lub większą.  
  
 Gdy `CMapStringToOb` obiekt zostanie usunięty lub gdy jego elementy są usuwane, `CString` obiektów i `CObject` wskaźniki są usuwane. Obiektów, odwołuje się `CObject` wskaźniki nie są niszczone.  
  
 Wyprowadzanie klasy mapy jest podobny do wyprowadzania listy. Zapoznaj się z artykułem [kolekcje](../../mfc/collections.md) ilustrację pochodnym klasy listy specjalnych.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CMapStringToOb`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxcoll.h  
  
##  <a name="cmapstringtoob"></a>  CMapStringToOb::CMapStringToOb  
 Tworzy pustą `CString`- do - `CObject*` mapy.  
  
```  
CMapStringToOb(INT_PTR nBlockSize = 10);
```  
  
### <a name="parameters"></a>Parametry  
 *nBlockSize*  
 Określa stopień szczegółowości alokacji pamięci do rozszerzania możliwości programu na mapie.  
  
### <a name="remarks"></a>Uwagi  
 Wraz z rozwojem mapy pamięć została przydzielona w jednostkach *nBlockSize* wpisów.  
  
 W poniższej tabeli przedstawiono innego członka funkcje, które są podobne do `CMapStringToOb:: CMapStringToOb`.  
  
|Class|Funkcja elementów członkowskich|  
|-----------|---------------------|  
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**CMapPtrToPtr( INT_PTR** `nBlockSize` **= 10 );**|  
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**CMapPtrToWord( INT_PTR** `nBlockSize` **= 10 );**|  
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**CMapStringToPtr( INT_PTR** `nBlockSize` **= 10 );**|  
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**CMapStringToString( INT_PTR** `nBlockSize` **= 10 );**|  
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**CMapWordToOb( INT_PTR** `nBlockSize` **= 10 );**|  
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**MapWordToPtr( INT_PTR** `nBlockSize` **= 10 );**|  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCCollections#63](../../mfc/codesnippet/cpp/cmapstringtoob-class_1.cpp)]  
  
 Zobacz [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) listę `CAge` klasa używana we wszystkich przykładach w kolekcji.  
  
##  <a name="getcount"></a>  CMapStringToOb::GetCount  
 Określa liczbę elementów w mapie.  
  
```  
INT_PTR GetCount() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczba elementów na tej mapie.  
  
### <a name="remarks"></a>Uwagi  
 W poniższej tabeli przedstawiono innego członka funkcje, które są podobne do `CMapStringToOb::GetCount`.  
  
|Class|Funkcja elementów członkowskich|  
|-----------|---------------------|  
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**INT_PTR GetCount () const;**|  
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**INT_PTR GetCount () const;**|  
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**INT_PTR GetCount () const;**|  
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**INT_PTR GetCount () const;**|  
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**INT_PTR GetCount () const;**|  
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**INT_PTR GetCount () const;**|  
  
### <a name="example"></a>Przykład  
 Zobacz [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) listę `CAge` klasa używana we wszystkich przykładach w kolekcji.  
  
 [!code-cpp[NVC_MFCCollections#64](../../mfc/codesnippet/cpp/cmapstringtoob-class_2.cpp)]  
  
##  <a name="gethashtablesize"></a>  CMapStringToOb::GetHashTableSize  
 Określa aktualną liczbę elementów w tabeli wyznaczania wartości skrótu.  
  
```  
UINT GetHashTableSize() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca liczbę elementów w tabeli wyznaczania wartości skrótu.  
  
### <a name="remarks"></a>Uwagi  
 W poniższej tabeli przedstawiono innego członka funkcje, które są podobne do `CMapStringToOb::GetHashTableSize`.  
  
|Class|Funkcja elementów członkowskich|  
|-----------|---------------------|  
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**UINT GetHashTableSize () const;**|  
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**UINT GetHashTableSize () const;**|  
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**UINT GetHashTableSize () const;**|  
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**UINT GetHashTableSize () const;**|  
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**UINT GetHashTableSize () const;**|  
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**UINT GetHashTableSize () const;**|  
  
##  <a name="getnextassoc"></a>  CMapStringToOb::GetNextAssoc  
 Pobiera element mapy w *rNextPosition*, następnie aktualizuje *rNextPosition* do odwoływania się do następnego elementu w mapie.  
  
```  
void GetNextAssoc(
    POSITION& rNextPosition,  
    CString& rKey,  
    CObject*& rValue) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *rNextPosition*  
 Określa odwołanie do wartości pozycji zwrócony przez poprzednie `GetNextAssoc` lub `GetStartPosition` wywołania.  
  
 *rKey*  
 Określa klucz zwróconego elementu pobrane (ciąg).  
  
 *r-wartości*  
 Określa wartość elementu pobrane ( `CObject` wskaźnika). Aby uzyskać więcej informacji o tym parametrze, zobacz uwagi.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja jest najbardziej przydatne do iteracji na elementach na mapie. Należy pamiętać, że sekwencja pozycji niekoniecznie jest taka sama jak wartość klucza sekwencji.  
  
 Jeśli element pobrane jest ostatni w mapie, nowa wartość *rNextPosition* ma wartość NULL.  
  
 Dla *rValue* parametru, pamiętaj rzutować typu obiektu do **CObject\*&**, czyli co wymaga kompilatora, jak pokazano w poniższym przykładzie:  
  
 [!code-cpp[NVC_MFCCollections#65](../../mfc/codesnippet/cpp/cmapstringtoob-class_3.cpp)]  
  
 To nie jest prawdziwa `GetNextAssoc` dla map, oparte na szablonach.  
  
 W poniższej tabeli przedstawiono innego członka funkcje, które są podobne do `CMapStringToOb::GetNextAssoc`.  
  
|Class|Funkcja elementów członkowskich|  
|-----------|---------------------|  
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**void GetNextAssoc (pozycja &** *rNextPosition* **, void\* &**  *rKey* **, void\* &**  *rValue* **) const;**|  
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**void GetNextAssoc (pozycja &** *rNextPosition* **, void\* &**  *rKey* **, WORD i** *rValue* **) const;**|  
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**void GetNextAssoc (pozycja &** *rNextPosition* **, CString &** *rKey* **, void\* &**  *rValue* **) const;**|  
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**void GetNextAssoc (pozycja &** *rNextPosition* **, CString &** *rKey* **, CString &** *rValue* **) const;**|  
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**void GetNextAssoc (pozycja &** *rNextPosition* **, WORD &** *rKey* **, CObject\* &**  *rValue* **) const;**|  
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**void GetNextAssoc (pozycja &** *rNextPosition* **, WORD &** *rKey* **, void\* &**  *rValue* **) const;**|  
  
### <a name="example"></a>Przykład  
 Zobacz [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) listę `CAge` klasa używana we wszystkich przykładach w kolekcji.  
  
 [!code-cpp[NVC_MFCCollections#66](../../mfc/codesnippet/cpp/cmapstringtoob-class_4.cpp)]  
  
 Wyniki z tego programu są następujące:  
  
 `Lisa : a CAge at $4724 11`  
  
 `Marge : a CAge at $47A8 35`  
  
 `Homer : a CAge at $4766 36`  
  
 `Bart : a CAge at $45D4 13`  
  
##  <a name="getsize"></a>  CMapStringToOb::GetSize  
 Zwraca liczbę elementów mapy.  
  
```  
INT_PTR GetSize() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczba elementów w mapie.  
  
### <a name="remarks"></a>Uwagi  
 Wywołaj tę metodę, aby pobrać liczbę elementów w mapie.  
  
 W poniższej tabeli przedstawiono innego członka funkcje, które są podobne do `CMapStringToOb::GetSize`.  
  
|Class|Funkcja elementów członkowskich|  
|-----------|---------------------|  
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**INT_PTR getsize — () const;**|  
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**INT_PTR getsize — () const;**|  
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**INT_PTR getsize — () const;**|  
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**INT_PTR getsize — () const;**|  
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**INT_PTR getsize — () const;**|  
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**INT_PTR getsize — () const;**|  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCCollections#67](../../mfc/codesnippet/cpp/cmapstringtoob-class_5.cpp)]  
  
##  <a name="getstartposition"></a>  CMapStringToOb::GetStartPosition  
 Uruchamia iteracji mapy, zwracając wartość pozycji, które mogą być przekazywane do `GetNextAssoc` wywołania.  
  
```  
POSITION GetStartPosition() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość pozycji, która wskazuje pozycja początkowa które mapy; lub wartość NULL, jeśli mapa jest pusta.  
  
### <a name="remarks"></a>Uwagi  
 Sekwencja iteracji nie jest przewidywalne; Dlatego "pierwszego elementu w mapie" ma specjalnego znaczenia.  
  
 W poniższej tabeli przedstawiono innego członka funkcje, które są podobne do `CMapStringToOb::GetStartPosition`.  
  
|Class|Funkcja elementów członkowskich|  
|-----------|---------------------|  
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**Pozycja GetStartPosition () const;**|  
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**Pozycja GetStartPosition () const;**|  
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**Pozycja GetStartPosition () const;**|  
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**Pozycja GetStartPosition () const;**|  
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**Pozycja GetStartPosition () const;**|  
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**Pozycja GetStartPosition () const;**|  
  
### <a name="example"></a>Przykład  
 Zobacz przykład [CMapStringToOb::GetNextAssoc](#getnextassoc).  
  
##  <a name="hashkey"></a>  CMapStringToOb::HashKey  
 Oblicza wartość skrótu dla określonego klucza.  
  
```  
UINT HashKey(LPCTSTR key) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *Klucz*  
 Klucz, którego wartość skrótu, które ma zostać obliczona.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość skrótu klucza  
  
### <a name="remarks"></a>Uwagi  
 W poniższej tabeli przedstawiono innego członka funkcje, które są podobne do `CMapStringToOb::HashKey`.  
  
|Class|Funkcja elementów członkowskich|  
|-----------|---------------------|  
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**UINT HashKey (void** <strong>\*</strong> `key` **) const;**|  
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**UINT HashKey (void** <strong>\*</strong> `key` **) const;**|  
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**UINT HashKey (LPCTSTR** `key` **) const;**|  
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**UINT HashKey (LPCTSTR** `key` **) const;**|  
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**UINT HashKey (program WORD** `key` **) const;**|  
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**UINT HashKey (program WORD** `key` **) const;**|  
  
##  <a name="inithashtable"></a>  CMapStringToOb::InitHashTable  
 Inicjuje tabelę mieszania.  
  
```  
void InitHashTable(
    UINT hashSize,  
    BOOL bAllocNow = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 *hashSize*  
 Liczba wpisów w tabeli wyznaczania wartości skrótu.  
  
 *bAllocNow*  
 W przypadku opcji TRUE przydziela tablicy skrótów po zainicjowaniu; w przeciwnym razie tabeli jest przydzielany, gdy potrzebne.  
  
### <a name="remarks"></a>Uwagi  
 Aby uzyskać najlepszą wydajność rozmiar tabeli wyznaczania wartości skrótu powinien być liczba pierwsza. Aby zminimalizować konflikty, rozmiar powinien być około 20% większa niż największa przewidywanego zestawu danych.  
  
 W poniższej tabeli przedstawiono innego członka funkcje, które są podobne do `CMapStringToOb::InitHashTable`.  
  
|Class|Funkcja elementów członkowskich|  
|-----------|---------------------|  
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**void InitHashTable (UINT** `hashSize` **, BOOL** `bAllocNow` **= TRUE);**|  
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**void InitHashTable (UINT** `hashSize` **, BOOL** `bAllocNow` **= TRUE);**|  
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**void InitHashTable (UINT** `hashSize` **, BOOL** `bAllocNow` **= TRUE);**|  
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**void InitHashTable (UINT** `hashSize` **, BOOL** `bAllocNow` **= TRUE);**|  
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**void InitHashTable (UINT** `hashSize` **, BOOL** `bAllocNow` **= TRUE);**|  
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**void InitHashTable (UINT** `hashSize` **, BOOL** `bAllocNow` **= TRUE);**|  
  
##  <a name="isempty"></a>  CMapStringToOb::IsEmpty  
 Określa, czy mapa jest pusta.  
  
```  
BOOL IsEmpty() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli to mapowanie nie zawiera elementów; w przeciwnym razie 0.  
  
### <a name="example"></a>Przykład  
 Zobacz przykład [RemoveAll](#removeall).  
  
### <a name="remarks"></a>Uwagi  
 W poniższej tabeli przedstawiono innego członka funkcje, które są podobne do **CMapStringToOb:: IsEmpty**.  
  
|Class|Funkcja elementów członkowskich|  
|-----------|---------------------|  
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**Wartość logiczna IsEmpty () const;**|  
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**Wartość logiczna IsEmpty () const;**|  
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**Wartość logiczna IsEmpty () const;**|  
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**Wartość logiczna IsEmpty () const;**|  
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**Wartość logiczna IsEmpty () const;**|  
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**Wartość logiczna IsEmpty () const;**|  
  
##  <a name="lookup"></a>  CMapStringToOb::Lookup  
 Zwraca `CObject` wskaźnika na podstawie `CString` wartości.  
  
```  
BOOL Lookup(
    LPCTSTR key,  
    CObject*& rValue) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *Klucz*  
 Określa klucz ciąg, który identyfikuje elementu, który ma być wyszukiwana.  
  
 *r-wartości*  
 Określa wartość zwrócona z elementu oglądałem się w górę.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli element został znaleziony; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 `Lookup` używa algorytmu wyznaczania wartości skrótu, aby szybko znaleźć element mapy za pomocą klucza, który dokładnie pasuje ( `CString` wartości).  
  
 W poniższej tabeli przedstawiono innego członka funkcje, które są podobne do `CMapStringToOb::LookUp`.  
  
|Class|Funkcja elementów członkowskich|  
|-----------|---------------------|  
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**Wyszukiwanie BOOL (void** <strong>\*</strong> `key` **, void\* &**  `rValue` **) const;**|  
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**Wyszukiwanie BOOL (void** <strong>\*</strong> `key` **, WORD &** `rValue` **) const;**|  
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**Wyszukiwanie BOOL (LPCTSTR** `key` **, void\* &**  `rValue` **) const;**|  
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**Wyszukiwanie BOOL (LPCTSTR** `key` **, CString &** `rValue` **) const;**|  
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**Wyszukiwanie BOOL (program WORD** `key` **, CObject\* &**  `rValue` **) const;**|  
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**Wyszukiwanie BOOL (program WORD** `key` **, void\* &**  `rValue` **) const;**|  
  
### <a name="example"></a>Przykład  
 Zobacz [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) listę `CAge` klasa używana we wszystkich przykładach w kolekcji.  
  
 [!code-cpp[NVC_MFCCollections#68](../../mfc/codesnippet/cpp/cmapstringtoob-class_6.cpp)]  
  
##  <a name="lookupkey"></a>  CMapStringToOb::LookupKey  
 Zwraca odwołanie do klucz skojarzony z określoną wartością klucza.  
  
```  
BOOL LookupKey(
    LPCTSTR key,  
    LPCTSTR& rKey) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *Klucz*  
 Określa klucz ciąg, który identyfikuje elementu, który ma być wyszukiwana.  
  
 *rKey*  
 Odwołanie do skojarzonego klucza.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli klucz został znaleziony; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Za pomocą odwołania do klucza jest niebezpieczne, jeśli są używane po skojarzony element został usunięty z mapy lub po mapy została zniszczona.  
  
 W poniższej tabeli przedstawiono innego członka funkcje, które są podobne do `CMapStringToOb:: LookupKey`.  
  
|Class|Funkcja elementów członkowskich|  
|-----------|---------------------|  
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**BOOL LookupKey (LPCTSTR** `key` **, LPCTSTR &** `rKey` **) const;**|  
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**BOOL LookupKey (LPCTSTR** `key` **, LPCTSTR &** `rKey` **) const;**|  
  
##  <a name="operator_at"></a>  [] CMapStringToOb::operator  
 Zastępuje wygodne `SetAt` funkcja elementu członkowskiego.  
  
```  
CObject*& operator[ ](lpctstr key);
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Odwołanie do wskaźnika do `CObject` obiektu lub wartość NULL, jeśli mapa jest pusta lub *klucz* znajduje się poza zakresem.  
  
### <a name="remarks"></a>Uwagi  
 Dlatego może służyć tylko z lewej instrukcji przypisania (l wartości). Jeśli nie ma żadnego elementu na mapie, z określonym kluczem, nowy element zostanie utworzony.  
  
 Istnieje nie "po prawej stronie" (r) odpowiednikiem tego operatora, ponieważ istnieje możliwość, że nie można znaleźć klucza w mapie. Użyj `Lookup` funkcja elementu członkowskiego do elementu pobierania.  
  
 W poniższej tabeli przedstawiono innego członka funkcje, które są podobne do `CMapStringToOb::operator []`.  
  
|Class|Funkcja elementów członkowskich|  
|-----------|---------------------|  
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|<strong>void\*& — operator\[] (void \*</strong>  `key`  **\);**|  
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**WORD & operator\[] (void** <strong>\*</strong> `key`  **\);**|  
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**void\*& — operator\[] (lpctstr** `key`  **\);**|  
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**Cstring — & — operator\[] (lpctstr** `key`  **\);**|  
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**CObject\*& — operator\[] (program word** `key`  **\);**|  
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**void\*& — operator\[] (program word** `key`  **\);**|  
  
### <a name="example"></a>Przykład  
 Zobacz [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) listę `CAge` klasa używana we wszystkich przykładach w kolekcji.  
  
 [!code-cpp[NVC_MFCCollections#72](../../mfc/codesnippet/cpp/cmapstringtoob-class_7.cpp)]  
  
 Wyniki z tego programu są następujące:  
  
 `Operator [] example: A CMapStringToOb with 2 elements`  
  
 `[Lisa] = a CAge at $4A02 11`  
  
 `[Bart] = a CAge at $497E 13`  
  
##  <a name="removeall"></a>  CMapStringToOb::RemoveAll  
 Usuwa wszystkie elementy z tej mapy i niszczy `CString` klucza obiektów.  
  
```  
void RemoveAll();
```  
  
### <a name="remarks"></a>Uwagi  
 `CObject` Przywoływane przez każdy klucz obiekty nie są niszczone. `RemoveAll` Funkcji może spowodować przecieki pamięci, jeśli użytkownik nie upewnij się, że występujących w odwołaniu `CObject` obiekty są niszczone.  
  
 Funkcja działa prawidłowo, jeśli mapa jest pusty.  
  
 W poniższej tabeli przedstawiono innego członka funkcje, które są podobne do `CMapStringToOb::RemoveAll`.  
  
|Class|Funkcja elementów członkowskich|  
|-----------|---------------------|  
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**void RemoveAll( );**|  
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**void RemoveAll( );**|  
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**void RemoveAll( );**|  
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**void RemoveAll( );**|  
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**void RemoveAll( );**|  
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**void RemoveAll( );**|  
  
### <a name="example"></a>Przykład  
 Zobacz [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) listę `CAge` klasa używana we wszystkich przykładach w kolekcji.  
  
 [!code-cpp[NVC_MFCCollections#69](../../mfc/codesnippet/cpp/cmapstringtoob-class_8.cpp)]  
  
##  <a name="removekey"></a>  CMapStringToOb::RemoveKey  
 Wyszukuje wpisu mapowania odpowiadający podany klucz; następnie Jeśli klucz zostanie znaleziony, usuwa wpis.  
  
```  
BOOL RemoveKey(LPCTSTR key);
```  
  
### <a name="parameters"></a>Parametry  
 *Klucz*  
 Określa ciąg używany do wyszukiwania na mapie.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli wpis zostało znalezione i pomyślnie usunął; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Może to powodować przecieki pamięci, jeśli `CObject` obiekt nie zostanie usunięty gdzie indziej.  
  
 W poniższej tabeli przedstawiono innego członka funkcje, które są podobne do `CMapStringToOb::RemoveKey`.  
  
|Class|Funkcja elementów członkowskich|  
|-----------|---------------------|  
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**BOOL RemoveKey (void** <strong>\*</strong> `key` **);**|  
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**BOOL RemoveKey (void** <strong>\*</strong> `key` **);**|  
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**BOOL RemoveKey (LPCTSTR** `key` **);**|  
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**BOOL RemoveKey (LPCTSTR** `key` **);**|  
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**BOOL RemoveKey (program WORD** `key` **);**|  
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**BOOL RemoveKey (program WORD** `key` **);**|  
  
### <a name="example"></a>Przykład  
 Zobacz [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) listę `CAge` klasa używana we wszystkich przykładach w kolekcji.  
  
 [!code-cpp[NVC_MFCCollections#70](../../mfc/codesnippet/cpp/cmapstringtoob-class_9.cpp)]  
  
 Wyniki z tego programu są następujące:  
  
 `RemoveKey example: A CMapStringToOb with 3 elements`  
  
 `[Marge] = a CAge at $49A0 35`  
  
 `[Homer] = a CAge at $495E 36`  
  
 `[Bart] = a CAge at $4634 13`  
  
##  <a name="setat"></a>  CMapStringToOb::SetAt  
 Podstawowy oznacza, że można wstawić elementu na mapie.  
  
```  
void SetAt(
    LPCTSTR key,  
    CObject* newValue);
```  
  
### <a name="parameters"></a>Parametry  
 *Klucz*  
 Określa ciąg, który jest kluczem nowego elementu.  
  
 *newValue*  
 Określa `CObject` wskaźnika, który jest wartością nowego elementu.  
  
### <a name="remarks"></a>Uwagi  
 Najpierw jest wyszukiwana klucza. Jeśli klucz zostanie znaleziony, a następnie odpowiednią wartość zostanie zmieniona; w przeciwnym razie zostanie utworzony nowy element pary klucz wartość.  
  
 W poniższej tabeli przedstawiono innego członka funkcje, które są podobne do `CMapStringToOb::SetAt`.  
  
|Class|Funkcja elementów członkowskich|  
|-----------|---------------------|  
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**void SetAt (void** <strong>\*</strong> `key` **, void** <strong>\*</strong> `newValue` **);**|  
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**void SetAt (void** <strong>\*</strong> `key` **, WORD** `newValue` **);**|  
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**void SetAt (LPCTSTR** `key` **, void** <strong>\*</strong> `newValue` **);**|  
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**void SetAt (LPCTSTR** `key` **, LPCTSTR** `newValue` **);**|  
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**void SetAt (program WORD** `key` **, CObject** <strong>\*</strong> `newValue` **);**|  
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**void SetAt (program WORD** `key` **, void** <strong>\*</strong> `newValue` **);**|  
  
### <a name="example"></a>Przykład  
 Zobacz [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) listę `CAge` klasa używana we wszystkich przykładach w kolekcji.  
  
 [!code-cpp[NVC_MFCCollections#71](../../mfc/codesnippet/cpp/cmapstringtoob-class_10.cpp)]  
  
 Wyniki z tego programu są następujące:  
  
 `before Lisa's birthday: A CMapStringToOb with 2 elements`  
  
 `[Lisa] = a CAge at $493C 11`  
  
 `[Bart] = a CAge at $4654 13`  
  
 `after Lisa's birthday: A CMapStringToOb with 2 elements`  
  
 `[Lisa] = a CAge at $49C0 12`  
  
 `[Bart] = a CAge at $4654 13`  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa CObject](../../mfc/reference/cobject-class.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasa CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)   
 [Klasa CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)   
 [Klasa CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)   
 [Klasa CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)   
 [Klasa CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)   
 [Klasa CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)
