---
title: Klasa CMapStringToOb | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
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
dev_langs: C++
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
caps.latest.revision: "20"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 1a840677819710247e73aa8e3bcb904be756f852
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="cmapstringtoob-class"></a>Klasa CMapStringToOb
Klasy kolekcji słownik mapujący unikatowy `CString` obiekty do `CObject` wskaźników.  
  
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
|[CMapStringToOb::GetHashTableSize](#gethashtablesize)|Określa bieżąca liczba elementów w tablicy skrótów.|  
|[CMapStringToOb::GetNextAssoc](#getnextassoc)|Pobiera następnego elementu potrzeby iteracji.|  
|[CMapStringToOb::GetSize](#getsize)|Zwraca liczbę elementów na tej mapie.|  
|[CMapStringToOb::GetStartPosition](#getstartposition)|Zwraca pozycję pierwszego elementu.|  
|[CMapStringToOb::HashKey](#hashkey)|Oblicza wartość skrótu z określonym kluczem.|  
|[CMapStringToOb::InitHashTable](#inithashtable)|Inicjuje tablicy skrótów.|  
|[CMapStringToOb::IsEmpty](#isempty)|Testy dla warunku pusta Mapa (Brak elementów).|  
|[CMapStringToOb::Lookup](#lookup)|Wyszukuje void wskaźnik oparte na kluczu wskaźnika typu void. Wartość wskaźnika, nie jednostki, który wskazuje, służy do porównywania klucza.|  
|[CMapStringToOb::LookupKey](#lookupkey)|Zwraca odwołanie do klucz skojarzony z określoną wartością klucza.|  
|[CMapStringToOb::RemoveAll](#removeall)|Usuwa wszystkie elementy z tej mapy.|  
|[CMapStringToOb::RemoveKey](#removekey)|Usuwa element określony przez klucz.|  
|[CMapStringToOb::SetAt](#setat)|Wstawia element do mapy; zastępuje istniejący element, jeśli dopasowany klucz zostanie znaleziony.|  
  
### <a name="public-operators"></a>Operatory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[[CMapStringToOb::operator]](#operator_at)|Wstawia element do mapy — operator podstawienia dla `SetAt`.|  
  
## <a name="remarks"></a>Uwagi  
 Po wstawieniu `CString` -  `CObject*` pary (element) do mapy, można efektywnie pobrać lub usunąć pary za pomocą ciągu lub `CString` wartość jako klucza. Można również iteracja wszystkie elementy na mapie.  
  
 Zmienna typu **pozycji** jest używane do dostępu alternatywnego wpis w wszystkie odmiany mapy. Można użyć **pozycji** wpis "pamiętać" i do iteracji mapy. Może uważasz, że ten iteracji jest sekwencyjnych przez wartość klucza; nie jest. Sekwencja pobrane elementów jest nieokreślony.  
  
 `CMapStringToOb`zawiera `IMPLEMENT_SERIAL` makro do obsługi serializacji i zrzucanie swoich elementów. Każdy element jest serializowany z kolei jeśli mapy jest przechowywany w archiwum, za pomocą przeciążenia wstawiania (  **<<** ) — operator lub `Serialize` funkcję elementu członkowskiego.  
  
 Jeśli potrzebujesz diagnostycznych zrzut poszczególne elementy na mapie ( `CString` wartość i `CObject` zawartość), musisz ustawić głębokość kontekstu zrzutu 1 lub większą.  
  
 Gdy `CMapStringToOb` obiekt jest usunięty lub gdy jego elementy są usuwane, `CString` obiektów i `CObject` wskaźniki zostaną usunięte. Obiekty odwołuje się `CObject` wskaźniki nie zostaną zniszczone.  
  
 Mapy pochodnym klasy jest podobna do listy pochodnym. Zapoznaj się z artykułem [kolekcje](../../mfc/collections.md) ilustrację pochodnym klasy listy specjalnych.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CMapStringToOb`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxcoll.h  
  
##  <a name="cmapstringtoob"></a>CMapStringToOb::CMapStringToOb  
 Tworzy pustą `CString`- do - `CObject*` mapy.  
  
```  
CMapStringToOb(INT_PTR nBlockSize = 10);
```  
  
### <a name="parameters"></a>Parametry  
 `nBlockSize`  
 Określa poziom szczegółowości Alokacja pamięci dla rozszerzanie mapy.  
  
### <a name="remarks"></a>Uwagi  
 Wraz z rozwojem mapy, w jednostkach jest przydzielana pamięć `nBlockSize` wpisów.  
  
 W poniższej tabeli przedstawiono innego członka funkcje, które są podobne do **CMapStringToOb:: CMapStringToOb**.  
  
|Class|Funkcja elementów członkowskich|  
|-----------|---------------------|  
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**CMapPtrToPtr (INT_PTR** `nBlockSize` **= 10);**|  
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**CMapPtrToWord (INT_PTR** `nBlockSize` **= 10);**|  
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**CMapStringToPtr (INT_PTR** `nBlockSize` **= 10);**|  
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**CMapStringToString (INT_PTR** `nBlockSize` **= 10);**|  
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**CMapWordToOb (INT_PTR** `nBlockSize` **= 10);**|  
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**MapWordToPtr (INT_PTR** `nBlockSize` **= 10);**|  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCCollections#63](../../mfc/codesnippet/cpp/cmapstringtoob-class_1.cpp)]  
  
 Zobacz [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) listę `CAge` klasa używana w wszystkie przykłady w kolekcji.  
  
##  <a name="getcount"></a>CMapStringToOb::GetCount  
 Określa, ile elementów są na mapie.  
  
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
 Zobacz [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) listę `CAge` klasa używana w wszystkie przykłady w kolekcji.  
  
 [!code-cpp[NVC_MFCCollections#64](../../mfc/codesnippet/cpp/cmapstringtoob-class_2.cpp)]  
  
##  <a name="gethashtablesize"></a>CMapStringToOb::GetHashTableSize  
 Określa bieżąca liczba elementów w tablicy skrótów.  
  
```  
UINT GetHashTableSize() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca liczbę elementów w tablicy skrótów.  
  
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
  
##  <a name="getnextassoc"></a>CMapStringToOb::GetNextAssoc  
 Pobiera element mapy pod *rNextPosition*, następnie aktualizuje *rNextPosition* do odwoływania się do następnego elementu na mapie.  
  
```  
void GetNextAssoc(
    POSITION& rNextPosition,  
    CString& rKey,  
    CObject*& rValue) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *rNextPosition*  
 Określa odwołania do **pozycji** wartość zwrócona przez poprzednie **GetNextAssoc** lub **GetStartPosition** wywołania.  
  
 *rKey*  
 Określa klucz zwróconego elementu pobrane (ciąg).  
  
 *r-wartości*  
 Określa wartość elementu pobrane ( **CObject** wskaźnika). Aby uzyskać więcej informacji na temat tego parametru, zobacz uwagi.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja jest najbardziej przydatny w przypadku iteracja przez wszystkie elementy na mapie. Należy pamiętać, że sekwencji pozycji nie jest zawsze taki sam jak wartości klucza sekwencji.  
  
 Jeśli element pobrane przez ostatnie na mapie jest następnie nowa wartość *rNextPosition* ustawiono **NULL**.  
  
 Dla *prawostronnie* parametru, należy rzutować tego typu obiektu **CObject\*&**, czyli co wymaga kompilatora, jak pokazano w poniższym przykładzie:  
  
 [!code-cpp[NVC_MFCCollections#65](../../mfc/codesnippet/cpp/cmapstringtoob-class_3.cpp)]  
  
 Nie jest to istotne w **GetNextAssoc** map oparte na szablonach.  
  
 W poniższej tabeli przedstawiono innego członka funkcje, które są podobne do **CMapStringToOb::GetNextAssoc**.  
  
|Class|Funkcja elementów członkowskich|  
|-----------|---------------------|  
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**void GetNextAssoc (pozycja &** *rNextPosition* **, void\* &**  *rKey* **, void\* &**  *prawostronnie* **) const;**|  
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**void GetNextAssoc (pozycja &** *rNextPosition* **, void\* &**  *rKey* **, WORD &** *prawostronnie* **) const;**|  
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**void GetNextAssoc (pozycja &** *rNextPosition* **, cstring — &** *rKey* **, void\* &**  *prawostronnie* **) const;**|  
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**void GetNextAssoc (pozycja &** *rNextPosition* **, cstring — &** *rKey* **, cstring — &** *prawostronnie* **) const;**|  
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**void GetNextAssoc (pozycja &** *rNextPosition* **, WORD &** *rKey* **, CObject\* &**  *prawostronnie* **) const;**|  
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**void GetNextAssoc (pozycja &** *rNextPosition* **, WORD &** *rKey* **, void\* &**  *prawostronnie* **) const;**|  
  
### <a name="example"></a>Przykład  
 Zobacz [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) listę `CAge` klasa używana w wszystkie przykłady w kolekcji.  
  
 [!code-cpp[NVC_MFCCollections#66](../../mfc/codesnippet/cpp/cmapstringtoob-class_4.cpp)]  
  
 Wyniki z tego programu są następujące:  
  
 `Lisa : a CAge at $4724 11`  
  
 `Marge : a CAge at $47A8 35`  
  
 `Homer : a CAge at $4766 36`  
  
 `Bart : a CAge at $45D4 13`  
  
##  <a name="getsize"></a>CMapStringToOb::GetSize  
 Zwraca liczbę elementów mapy.  
  
```  
INT_PTR GetSize() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczba elementów w planie.  
  
### <a name="remarks"></a>Uwagi  
 Wywołaj tę metodę, aby pobrać liczbę elementów w planie.  
  
 W poniższej tabeli przedstawiono innego członka funkcje, które są podobne do `CMapStringToOb::GetSize`.  
  
|Class|Funkcja elementów członkowskich|  
|-----------|---------------------|  
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**INT_PTR GetSize () const;**|  
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**INT_PTR GetSize () const;**|  
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**INT_PTR GetSize () const;**|  
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**INT_PTR GetSize () const;**|  
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**INT_PTR GetSize () const;**|  
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**INT_PTR GetSize () const;**|  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCCollections#67](../../mfc/codesnippet/cpp/cmapstringtoob-class_5.cpp)]  
  
##  <a name="getstartposition"></a>CMapStringToOb::GetStartPosition  
 Uruchamia iteracji mapy zwracając **pozycji** wartości, które mogą zostać przekazane do `GetNextAssoc` wywołania.  
  
```  
POSITION GetStartPosition() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 A **pozycji** wartość, która wskazuje pozycję początkową, które mapy; lub **NULL** Jeśli mapy jest pusta.  
  
### <a name="remarks"></a>Uwagi  
 Sekwencja iteracji nie jest przewidywalne; w związku z tym "pierwszy element w mapie" ma specjalnego znaczenia.  
  
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
  
##  <a name="hashkey"></a>CMapStringToOb::HashKey  
 Oblicza wartość skrótu z określonym kluczem.  
  
```  
UINT HashKey(LPCTSTR key) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `key`  
 Klucz wartości skrótu, którego ma zostać obliczona.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość skrótu klucza  
  
### <a name="remarks"></a>Uwagi  
 W poniższej tabeli przedstawiono innego członka funkcje, które są podobne do `CMapStringToOb::HashKey`.  
  
|Class|Funkcja elementów członkowskich|  
|-----------|---------------------|  
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**UINT HashKey (void\***  `key` **) const;**|  
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**UINT HashKey (void\***  `key` **) const;**|  
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**UINT HashKey (LPCTSTR** `key` **) const;**|  
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**UINT HashKey (LPCTSTR** `key` **) const;**|  
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**UINT HashKey (WORD** `key` **) const;**|  
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**UINT HashKey (WORD** `key` **) const;**|  
  
##  <a name="inithashtable"></a>CMapStringToOb::InitHashTable  
 Inicjuje tablicy skrótów.  
  
```  
void InitHashTable(
    UINT hashSize,  
    BOOL bAllocNow = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 `hashSize`  
 Liczba wpisów w tablicy skrótów.  
  
 `bAllocNow`  
 Jeśli **TRUE**, przydziela tablicy skrótów po zainicjowaniu; w przeciwnym razie tabeli jest przydzielane w razie potrzeby.  
  
### <a name="remarks"></a>Uwagi  
 Aby uzyskać najlepszą wydajność rozmiar tabeli skrótów powinna być liczba pierwsza. Aby zminimalizować problemy, rozmiar powinien mieścić się około 20 procent większy niż największy oczekiwanego zestawu danych.  
  
 W poniższej tabeli przedstawiono innego członka funkcje, które są podobne do `CMapStringToOb::InitHashTable`.  
  
|Class|Funkcja elementów członkowskich|  
|-----------|---------------------|  
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**void InitHashTable (UINT** `hashSize` **, BOOL** `bAllocNow` **= TRUE);**|  
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**void InitHashTable (UINT** `hashSize` **, BOOL** `bAllocNow` **= TRUE);**|  
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**void InitHashTable (UINT** `hashSize` **, BOOL** `bAllocNow` **= TRUE);**|  
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**void InitHashTable (UINT** `hashSize` **, BOOL** `bAllocNow` **= TRUE);**|  
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**void InitHashTable (UINT** `hashSize` **, BOOL** `bAllocNow` **= TRUE);**|  
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**void InitHashTable (UINT** `hashSize` **, BOOL** `bAllocNow` **= TRUE);**|  
  
##  <a name="isempty"></a>CMapStringToOb::IsEmpty  
 Określa, czy mapa jest pusta.  
  
```  
BOOL IsEmpty() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli ta mapa nie zawiera żadnych elementów; w przeciwnym razie 0.  
  
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
  
##  <a name="lookup"></a>CMapStringToOb::Lookup  
 Zwraca `CObject` wskaźnika na podstawie `CString` wartości.  
  
```  
BOOL Lookup(
    LPCTSTR key,  
    CObject*& rValue) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `key`  
 Określa klucz ciąg identyfikujący elementu, który ma być wyszukiwane.  
  
 `rValue`  
 Określa wartość zwrócona z elementu wyszukiwanego w górę.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli znaleziono element; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 `Lookup`używa algorytmu wyznaczania wartości skrótu można szybko znaleźć za pomocą klucza dokładnie pasujący map element ( `CString` wartości).  
  
 W poniższej tabeli przedstawiono innego członka funkcje, które są podobne do `CMapStringToOb::LookUp`.  
  
|Class|Funkcja elementów członkowskich|  
|-----------|---------------------|  
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**Wyszukiwanie BOOL (void\***  `key` **, void\* &**  `rValue` **) const;**|  
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**Wyszukiwanie BOOL (void\***  `key` **, WORD &** `rValue` **) const;**|  
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**Wyszukiwanie BOOL (LPCTSTR** `key` **, void\* &**  `rValue` **) const;**|  
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**Wyszukiwanie BOOL (LPCTSTR** `key` **, cstring — &** `rValue` **) const;**|  
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**Wyszukiwanie BOOL (WORD** `key` **, CObject\* &**  `rValue` **) const;**|  
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**Wyszukiwanie BOOL (WORD** `key` **, void\* &**  `rValue` **) const;**|  
  
### <a name="example"></a>Przykład  
 Zobacz [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) listę `CAge` klasa używana w wszystkie przykłady w kolekcji.  
  
 [!code-cpp[NVC_MFCCollections#68](../../mfc/codesnippet/cpp/cmapstringtoob-class_6.cpp)]  
  
##  <a name="lookupkey"></a>CMapStringToOb::LookupKey  
 Zwraca odwołanie do klucz skojarzony z określoną wartością klucza.  
  
```  
BOOL LookupKey(
    LPCTSTR key,  
    LPCTSTR& rKey) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `key`  
 Określa klucz ciąg identyfikujący elementu, który ma być wyszukiwane.  
  
 `rKey`  
 Odwołanie do skojarzony klucz.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli znaleziono klucz; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Przy użyciu odwołania do klucza jest niebezpieczne, jeśli są używane po skojarzony element został usunięty z mapy lub po mapy została zniszczona.  
  
 W poniższej tabeli przedstawiono innego członka funkcje, które są podobne do **CMapStringToOb:: LookupKey**.  
  
|Class|Funkcja elementów członkowskich|  
|-----------|---------------------|  
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**BOOL LookupKey (LPCTSTR** `key` **, LPCTSTR &** `rKey` **) const;**|  
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**BOOL LookupKey (LPCTSTR** `key` **, LPCTSTR &** `rKey` **) const;**|  
  
##  <a name="operator_at"></a>[CMapStringToOb::operator]  
 Zastępuje wygodne `SetAt` funkcję elementu członkowskiego.  
  
```  
CObject*& operator[ ](lpctstr key);
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Odwołanie do wskaźnika do `CObject` obiekt; lub **NULL** Jeśli mapy jest pusta lub `key` jest poza zakresem.  
  
### <a name="remarks"></a>Uwagi  
 W związku z tym można używać tylko po lewej stronie instrukcji przypisania (wartością l-value). Jeśli nie ma mapy elementu z określonym kluczem, jest tworzony nowy element.  
  
 Nie jest równoważna tego operatora nie "po prawej stronie" (r), ponieważ istnieje możliwość, że nie można odnaleźć klucza na mapie. Użyj `Lookup` funkcji członkowskiej dla elementu pobierania.  
  
 W poniższej tabeli przedstawiono innego członka funkcje, które są podobne do **[CMapStringToOb::operator]**.  
  
|Class|Funkcja elementów członkowskich|  
|-----------|---------------------|  
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**void\*& — operator [] (void\***  `key`  **\);**|  
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**WORD & — operator [] (void\***  `key`  **\);**|  
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**void\*& — operator [] (lpctstr** `key`  **\);**|  
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**Cstring — & — operator [] (lpctstr** `key`  **\);**|  
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**CObject\*& — operator [] (word** `key`  **\);**|  
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**void\*& — operator [] (word** `key`  **\);**|  
  
### <a name="example"></a>Przykład  
 Zobacz [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) listę `CAge` klasa używana w wszystkie przykłady w kolekcji.  
  
 [!code-cpp[NVC_MFCCollections#72](../../mfc/codesnippet/cpp/cmapstringtoob-class_7.cpp)]  
  
 Wyniki z tego programu są następujące:  
  
 `Operator [] example: A CMapStringToOb with 2 elements`  
  
 `[Lisa] = a CAge at $4A02 11`  
  
 `[Bart] = a CAge at $497E 13`  
  
##  <a name="removeall"></a>CMapStringToOb::RemoveAll  
 Usuwa wszystkie elementy z tej mapy i niszczy `CString` klucza obiektów.  
  
```  
void RemoveAll();
```  
  
### <a name="remarks"></a>Uwagi  
 `CObject` Obiektów odwołuje się każdy klucz nie zostaną zniszczone. `RemoveAll` Funkcja może powodować przecieki pamięci, jeśli użytkownik nie upewnij się, że przywoływana `CObject` obiekty zostaną zniszczone.  
  
 Funkcja działa prawidłowo, jeśli mapy już jest pusta.  
  
 W poniższej tabeli przedstawiono innego członka funkcje, które są podobne do `CMapStringToOb::RemoveAll`.  
  
|Class|Funkcja elementów członkowskich|  
|-----------|---------------------|  
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**void RemoveAll ();**|  
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**void RemoveAll ();**|  
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**void RemoveAll ();**|  
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**void RemoveAll ();**|  
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**void RemoveAll ();**|  
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**void RemoveAll ();**|  
  
### <a name="example"></a>Przykład  
 Zobacz [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) listę `CAge` klasa używana w wszystkie przykłady w kolekcji.  
  
 [!code-cpp[NVC_MFCCollections#69](../../mfc/codesnippet/cpp/cmapstringtoob-class_8.cpp)]  
  
##  <a name="removekey"></a>CMapStringToOb::RemoveKey  
 Wyszukuje wpisu mapy odpowiadający podany klucz; następnie Jeśli klucz zostanie znaleziony, usuwa wpis.  
  
```  
BOOL RemoveKey(LPCTSTR key);
```  
  
### <a name="parameters"></a>Parametry  
 `key`  
 Określa ciąg używany do wyszukiwania mapy.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli wpis został znaleziony i pomyślnie usunął; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Może to powodować przecieki pamięci, jeśli `CObject` obiektu nie jest usuwany w innym miejscu.  
  
 W poniższej tabeli przedstawiono innego członka funkcje, które są podobne do `CMapStringToOb::RemoveKey`.  
  
|Class|Funkcja elementów członkowskich|  
|-----------|---------------------|  
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**BOOL RemoveKey (void\***  `key` **);**|  
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**BOOL RemoveKey (void\***  `key` **);**|  
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**BOOL RemoveKey (LPCTSTR** `key` **);**|  
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**BOOL RemoveKey (LPCTSTR** `key` **);**|  
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**BOOL RemoveKey (WORD** `key` **);**|  
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**BOOL RemoveKey (WORD** `key` **);**|  
  
### <a name="example"></a>Przykład  
 Zobacz [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) listę `CAge` klasa używana w wszystkie przykłady w kolekcji.  
  
 [!code-cpp[NVC_MFCCollections#70](../../mfc/codesnippet/cpp/cmapstringtoob-class_9.cpp)]  
  
 Wyniki z tego programu są następujące:  
  
 `RemoveKey example: A CMapStringToOb with 3 elements`  
  
 `[Marge] = a CAge at $49A0 35`  
  
 `[Homer] = a CAge at $495E 36`  
  
 `[Bart] = a CAge at $4634 13`  
  
##  <a name="setat"></a>CMapStringToOb::SetAt  
 Podstawowy oznacza, że wstawić element na mapie.  
  
```  
void SetAt(
    LPCTSTR key,  
    CObject* newValue);
```  
  
### <a name="parameters"></a>Parametry  
 `key`  
 Określa ciąg, który jest kluczem nowego elementu.  
  
 `newValue`  
 Określa `CObject` wskaźnika, która jest wartością nowego elementu.  
  
### <a name="remarks"></a>Uwagi  
 Po pierwsze wyszukiwania klucza. Jeśli klucz zostanie znaleziony, a następnie zostanie zmieniona wartość odpowiadająca; w przeciwnym razie jest tworzony nowy element klucz wartość.  
  
 W poniższej tabeli przedstawiono innego członka funkcje, które są podobne do `CMapStringToOb::SetAt`.  
  
|Class|Funkcja elementów członkowskich|  
|-----------|---------------------|  
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**void SetAt (void\***  `key` **, void\***  `newValue` **);**|  
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**void SetAt (void\***  `key` **, WORD** `newValue` **);**|  
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**void SetAt (LPCTSTR** `key` **, void\***  `newValue` **);**|  
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**void SetAt (LPCTSTR** `key` **, LPCTSTR** `newValue` **);**|  
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**void SetAt (WORD** `key` **, CObject\***  `newValue` **);**|  
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**void SetAt (WORD** `key` **, void\***  `newValue` **);**|  
  
### <a name="example"></a>Przykład  
 Zobacz [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) listę `CAge` klasa używana w wszystkie przykłady w kolekcji.  
  
 [!code-cpp[NVC_MFCCollections#71](../../mfc/codesnippet/cpp/cmapstringtoob-class_10.cpp)]  
  
 Wyniki z tego programu są następujące:  
  
 `before Lisa's birthday: A CMapStringToOb with 2 elements`  
  
 `[Lisa] = a CAge at $493C 11`  
  
 `[Bart] = a CAge at $4654 13`  
  
 `after Lisa's birthday: A CMapStringToOb with 2 elements`  
  
 `[Lisa] = a CAge at $49C0 12`  
  
 `[Bart] = a CAge at $4654 13`  
  
## <a name="see-also"></a>Zobacz też  
 [CObject — klasa](../../mfc/reference/cobject-class.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasa CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)   
 [Klasa CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)   
 [Klasa CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)   
 [Klasa CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)   
 [Klasa CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)   
 [Klasa CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)
