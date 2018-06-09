---
title: Klasa CMap | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMap
- AFXTEMPL/CMap
- AFXTEMPL/CMap::CPair
- AFXTEMPL/CMap::CMap
- AFXTEMPL/CMap::GetCount
- AFXTEMPL/CMap::GetHashTableSize
- AFXTEMPL/CMap::GetNextAssoc
- AFXTEMPL/CMap::GetSize
- AFXTEMPL/CMap::GetStartPosition
- AFXTEMPL/CMap::InitHashTable
- AFXTEMPL/CMap::IsEmpty
- AFXTEMPL/CMap::Lookup
- AFXTEMPL/CMap::PGetFirstAssoc
- AFXTEMPL/CMap::PGetNextAssoc
- AFXTEMPL/CMap::PLookup
- AFXTEMPL/CMap::RemoveAll
- AFXTEMPL/CMap::RemoveKey
- AFXTEMPL/CMap::SetAt
dev_langs:
- C++
helpviewer_keywords:
- CMap [MFC], CPair
- CMap [MFC], CMap
- CMap [MFC], GetCount
- CMap [MFC], GetHashTableSize
- CMap [MFC], GetNextAssoc
- CMap [MFC], GetSize
- CMap [MFC], GetStartPosition
- CMap [MFC], InitHashTable
- CMap [MFC], IsEmpty
- CMap [MFC], Lookup
- CMap [MFC], PGetFirstAssoc
- CMap [MFC], PGetNextAssoc
- CMap [MFC], PLookup
- CMap [MFC], RemoveAll
- CMap [MFC], RemoveKey
- CMap [MFC], SetAt
ms.assetid: 640a45ab-0993-4def-97ec-42cc78eb10b9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 89e508242e7318e5419656720b6dee20bed55716
ms.sourcegitcommit: 59afc95d0e494af658cf464503f7f89bd1a8d2ce
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2018
ms.locfileid: "35239427"
---
# <a name="cmap-class"></a>Klasa CMap
Klasa kolekcji słownik mapujący klucze unikatowe wartości.  
  
## <a name="syntax"></a>Składnia  
  
```  
template<class KEY, class ARG_KEY, class VALUE, class ARG_VALUE>class CMap : public CObject  
```  
  
#### <a name="parameters"></a>Parametry  
 `KEY`  
 Klasa Obiekt używany jako klucz do mapy.  
  
 `ARG_KEY`  
 Typ danych używany dla `KEY` argumentów; zwykle odwołanie do `KEY`.  
  
 `VALUE`  
 Klasa obiektu przechowywane na mapie.  
  
 `ARG_VALUE`  
 Typ danych używany dla `VALUE` argumentów; zwykle odwołanie do `VALUE`.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-structures"></a>Publiczny struktury  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CMap::CPair](#cpair)|Zagnieżdżone struktury zawierające wartości klucza i wartości skojarzonego obiektu.|  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CMap::CMap](#cmap)|Konstruuje kolekcję mapujący klucze do wartości.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CMap::GetCount](#getcount)|Zwraca liczbę elementów na tej mapie.|  
|[CMap::GetHashTableSize](#gethashtablesize)|Zwraca liczbę elementów w tablicy skrótów.|  
|[CMap::GetNextAssoc](#getnextassoc)|Pobiera następnego elementu potrzeby iteracji.|  
|[CMap::GetSize](#getsize)|Zwraca liczbę elementów na tej mapie.|  
|[CMap::GetStartPosition](#getstartposition)|Zwraca pozycję pierwszego elementu.|  
|[CMap::InitHashTable](#inithashtable)|Inicjuje tablicy skrótów i określa jego rozmiar.|  
|[CMap::IsEmpty](#isempty)|Testy dla warunku pusta Mapa (Brak elementów).|  
|[CMap::Lookup](#lookup)|Wyszukuje wartość mapowane na danym kluczem.|  
|[CMap::PGetFirstAssoc](#pgetfirstassoc)|Zwraca wskaźnik do pierwszego elementu.|  
|[CMap::PGetNextAssoc](#pgetnextassoc)|Pobiera wskaźnik do następnego elementu potrzeby iteracji.|  
|[CMap::PLookup](#plookup)|Zwraca wskaźnik do klucza, którego wartość odpowiada określonej wartości.|  
|[CMap::RemoveAll](#removeall)|Usuwa wszystkie elementy z tej mapy.|  
|[CMap::RemoveKey](#removekey)|Usuwa element określony przez klucz.|  
|[CMap::SetAt](#setat)|Wstawia element do mapy; zastępuje istniejący element, jeśli dopasowany klucz zostanie znaleziony.|  
  
### <a name="public-operators"></a>Operatory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[[CMap::operator]](#operator_at)|Wstawia element do mapy — operator podstawienia dla `SetAt`.|  
  
## <a name="remarks"></a>Uwagi  
 Po wstawieniu pary klucz wartość (element) do mapy wydajnie można pobrać lub usunąć pary przy użyciu klucza dostępu do niego. Można również iteracja wszystkie elementy na mapie.  
  
 Zmienna typu **pozycji** jest używana do alternatywnego dostępu do wpisów. Można użyć **pozycji** wpis "pamiętać" i do iteracji mapy. Może uważasz, że ten iteracji jest sekwencyjnych przez wartość klucza; nie jest. Sekwencja pobrane elementów jest nieokreślony.  
  
 Niektóre funkcje Członkowskie wywołanie klasy funkcje globalne pomocy, które muszą być dostosowane dla większości zastosowań `CMap` klasy. Zobacz [pomocnicy klasy kolekcji](../../mfc/reference/collection-class-helpers.md) w sekcji makra i funkcje globalne `MFC Reference`.  
  
 `CMap` zastępuje [CObject::Serialize](../../mfc/reference/cobject-class.md#serialize) do obsługi serializacji i zrzucanie swoich elementów. Jeśli mapy jest przechowywany przy użyciu archiwum `Serialize`, każdy element mapy jest serializowany z kolei. Domyślna implementacja `SerializeElements` funkcja pomocnicza jest logiczną zapisu. Dla informacje o serializacji elementów kolekcji wskaźnika pochodną `CObject` lub innych typów zdefiniowanych przez użytkownika, zobacz [porady: tworzenie bezpiecznej kolekcji](../../mfc/how-to-make-a-type-safe-collection.md).  
  
 Diagnostycznych zrzut poszczególne elementy na mapie (klucze i wartości), należy do co najmniej 1 należy ustawić głębokość kontekstu zrzutu.  
  
 Gdy `CMap` obiekt jest usunięty lub gdy jego elementy są usuwane, klucze i wartości zostaną usunięte.  
  
 Mapy pochodnym klasy jest podobna do listy pochodnym. Zapoznaj się z artykułem [kolekcje](../../mfc/collections.md) ilustrację pochodnym klasy listy specjalnych.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CMap`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxtempl.h  
  
##  <a name="cmap"></a>  CMap::CMap  
 Tworzy pusty mapy.  
  
```  
CMap(INT_PTR nBlockSize = 10);
```  
  
### <a name="parameters"></a>Parametry  
 `nBlockSize`  
 Określa poziom szczegółowości Alokacja pamięci dla rozszerzanie mapy.  
  
### <a name="remarks"></a>Uwagi  
 Wraz z rozwojem mapy, w jednostkach jest przydzielana pamięć `nBlockSize` wpisów.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCCollections#56](../../mfc/codesnippet/cpp/cmap-class_1.cpp)]  
  
##  <a name="cpair"></a>  CMap::CPair  
 Zawiera wartość klucza i wartość skojarzonego obiektu.  
  
### <a name="remarks"></a>Uwagi  
 To jest strukturą zagnieżdżone w obrębie klasy [CMap](../../mfc/reference/cmap-class.md).  
  
 Struktura składa się z dwóch pól:  
  
- **klucz** rzeczywistej wartości Typ klucza.  
  
- **wartość** wartość skojarzonego obiektu.  
  
 Jest on używany do przechowywania wartości zwracanych z [CMap::PLookup](#plookup), [CMap::PGetFirstAssoc](#pgetfirstassoc), i [CMap::PGetNextAssoc](#pgetnextassoc).  
  
### <a name="example"></a>Przykład  
 Przykład użycia, zobacz przykład [CMap::PLookup](#plookup).  
  
##  <a name="getcount"></a>  CMap::GetCount  
 Pobiera liczbę elementów w planie.  
  
```  
INT_PTR GetCount() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczba elementów.  
  
### <a name="example"></a>Przykład  
 Zobacz przykład [CMap::Lookup](#lookup).  
  
##  <a name="gethashtablesize"></a>  CMap::GetHashTableSize  
 Określa liczbę elementów w tablicy skrótów do mapy.  
  
```  
UINT GetHashTableSize() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczba elementów w tablicy skrótów.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCCollections#57](../../mfc/codesnippet/cpp/cmap-class_2.cpp)]  
  
##  <a name="getnextassoc"></a>  CMap::GetNextAssoc  
 Pobiera element mapy pod `rNextPosition`, następnie aktualizuje `rNextPosition` do odwoływania się do następnego elementu na mapie.  
  
```  
void GetNextAssoc(
    POSITION& rNextPosition,
    KEY& rKey,
    VALUE& rValue) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `rNextPosition`  
 Określa odwołania do **pozycji** wartość zwrócona przez poprzednie `GetNextAssoc` lub `GetStartPosition` wywołania.  
  
 *KEY*  
 Parametr szablonu określający typ klucza mapy.  
  
 `rKey`  
 Określa klucz zwróconego elementu pobrane.  
  
 *WARTOŚĆ*  
 Parametr szablonu określający typ wartości mapy.  
  
 `rValue`  
 Określa wartość elementu pobrane.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja jest najbardziej przydatny w przypadku iteracja przez wszystkie elementy na mapie. Należy pamiętać, że sekwencji pozycji nie jest zawsze taki sam jak wartości klucza sekwencji.  
  
 Jeśli element pobrane przez ostatnie na mapie jest następnie nowa wartość `rNextPosition` ustawiono **NULL**.  
  
### <a name="example"></a>Przykład  
 Zobacz przykład [CMap::SetAt](#setat).  
  
##  <a name="getsize"></a>  CMap::GetSize  
 Zwraca liczbę elementów mapy.  
  
```  
INT_PTR GetSize() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczba elementów w planie.  
  
### <a name="remarks"></a>Uwagi  
 Wywołaj tę metodę, aby pobrać liczbę elementów w planie.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCCollections#58](../../mfc/codesnippet/cpp/cmap-class_3.cpp)]  
  
##  <a name="getstartposition"></a>  CMap::GetStartPosition  
 Uruchamia iteracji mapy zwracając **pozycji** wartości, które mogą zostać przekazane do `GetNextAssoc` wywołania.  
  
```  
POSITION GetStartPosition() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 A **pozycji** wartość, która wskazuje pozycję początkową, które mapy; lub **NULL** Jeśli mapy jest pusta.  
  
### <a name="remarks"></a>Uwagi  
 Sekwencja iteracji nie jest przewidywalne; w związku z tym "pierwszy element w mapie" ma specjalnego znaczenia.  
  
### <a name="example"></a>Przykład  
 Zobacz przykład [CMap::SetAt](#setat).  
  
##  <a name="inithashtable"></a>  CMap::InitHashTable  
 Inicjuje tablicy skrótów.  
  
```  
void InitHashTable(UINT hashSize, BOOL  bAllocNow = TRUE);  
```  
  
### <a name="parameters"></a>Parametry  
 `hashSize`  
 Liczba wpisów w tablicy skrótów.  
  
 `bAllocNow`  
 Jeśli **TRUE**, przydziela tablicy skrótów po zainicjowaniu; w przeciwnym razie tabeli jest przydzielane w razie potrzeby.  
  
### <a name="remarks"></a>Uwagi  
 Aby uzyskać najlepszą wydajność rozmiar tabeli skrótów powinna być liczba pierwsza. Aby zminimalizować problemy, rozmiar powinien mieścić się około 20 procent większy niż największy oczekiwanego zestawu danych.  
  
### <a name="example"></a>Przykład  
 Zobacz przykład [CMap::Lookup](#lookup).  
  
##  <a name="isempty"></a>  CMap::IsEmpty  
 Określa, czy mapa jest pusta.  
  
```  
BOOL IsEmpty() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli ta mapa nie zawiera żadnych elementów; w przeciwnym razie 0.  
  
### <a name="example"></a>Przykład  
 Zobacz przykład [CMap::RemoveAll](#removeall).  
  
##  <a name="lookup"></a>  CMap::Lookup  
 Wyszukuje wartość mapowane na danym kluczem.  
  
```  
BOOL Lookup(ARG_KEY key, VALUE& rValue) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `ARG_KEY`  
 Parametr szablonu określenie typu `key` wartości.  
  
 `key`  
 Określa klucz identyfikujący element, aby wyszukiwać.  
  
 *WARTOŚĆ*  
 Określa typ wartości, aby wyszukiwać.  
  
 `rValue`  
 Odbiera wartość wyszukiwanego w górę.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli znaleziono element; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 `Lookup` używa algorytmu wyznaczania wartości skrótu, aby szybko znaleźć map element za pomocą klucza, która dokładnie odpowiada danym kluczem.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCCollections#58](../../mfc/codesnippet/cpp/cmap-class_3.cpp)]  
  
##  <a name="operator_at"></a>  [CMap::operator]  
 Zastępuje wygodne `SetAt` funkcję elementu członkowskiego.  
  
```  
VALUE& operator[](arg_key key);
```  
  
### <a name="parameters"></a>Parametry  
 *WARTOŚĆ*  
 Parametr szablonu określający typ wartości mapy.  
  
 `ARG_KEY`  
 Parametr szablonu określający typ wartości klucza.  
  
 `key`  
 Klucz używany do pobierania wartości z mapy.  
  
### <a name="remarks"></a>Uwagi  
 W związku z tym można używać tylko po lewej stronie instrukcji przypisania (wartością l-value). Jeśli nie ma mapy elementu z określonym kluczem, jest tworzony nowy element.  
  
 Nie jest równoważna tego operatora nie "po prawej stronie" (r), ponieważ istnieje możliwość, że nie można odnaleźć klucza na mapie. Użyj `Lookup` funkcji członkowskiej dla elementu pobierania.  
  
### <a name="example"></a>Przykład  
 Zobacz przykład [CMap::Lookup](#lookup).  
  
##  <a name="pgetfirstassoc"></a>  CMap::PGetFirstAssoc  
 Zwraca pierwszy wpis obiektu mapy.  
  
```  
const CPair* PGetFirstAssoc() const; 
CPair* PGetFirstAssoc();  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do pierwszego wpis w mapie; zobacz [CMap::CPair](#cpair). Jeśli mapy nie zawiera żadnych pozycji, wartość jest **NULL**.  
  
### <a name="remarks"></a>Uwagi  
 Wywołanie tej funkcji, aby zwracać wskaźnik pierwszego elementu w obiekcie mapy.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCCollections#59](../../mfc/codesnippet/cpp/cmap-class_4.cpp)]  
  
##  <a name="pgetnextassoc"></a>  CMap::PGetNextAssoc  
 Pobiera element map wskazywana przez `pAssocRec`.  
  
```  
const CPair *PGetNextAssoc(const CPair* pAssocRet) const;  
  
CPair *PGetNextAssoc(const CPair* pAssocRet);
```  
  
### <a name="parameters"></a>Parametry  
 *pAssocRet*  
 Wskazuje wpis mapy zwrócony przez poprzednie [PGetNextAssoc](#pgetnextassoc) lub [CMap::PGetFirstAssoc](#pgetfirstassoc) wywołania.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do następnego wpisu w mapowaniu; zobacz [CMap::CPair](#cpair). Jeśli element jest ostatni w planie, wartość jest **NULL**.  
  
### <a name="remarks"></a>Uwagi  
 Wywołaj tę metodę, aby wykonać iterację wszystkie elementy na mapie. Pierwszy element z wywołaniem do pobrania `PGetFirstAssoc` , a następnie wykonać iterację mapy kolejne wywołania `PGetNextAssoc`.  
  
### <a name="example"></a>Przykład  
 Zobacz przykład [CMap::PGetFirstAssoc](#pgetfirstassoc).  
  
##  <a name="plookup"></a>  CMap::PLookup  
 Wyszukuje wartość mapowane na danym kluczem.  
  
```  
const CPair* PLookup(ARG_KEY key) const;
CPair* PLookup(ARG_KEY key);  
```  
  
### <a name="parameters"></a>Parametry  
 `key`  
 Klucz dla elementu, który ma zostać wyszukany.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do struktury klucza; zobacz [CMap::CPair](#cpair). Jeśli nie znaleziono, `CMap::PLookup` zwraca `NULL`.  
  
### <a name="remarks"></a>Uwagi  
 Wywołaj tę metodę, aby wyszukać map element, za pomocą klucza, która dokładnie odpowiada danym kluczem.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCCollections#60](../../mfc/codesnippet/cpp/cmap-class_5.cpp)]  
  
##  <a name="removeall"></a>  CMap::RemoveAll  
 Usuwa wszystkie wartości z tej mapy przez wywołanie funkcji pomocnika globalne **destructelements —**.  
  
```  
void RemoveAll();
```  
  
### <a name="remarks"></a>Uwagi  
 Funkcja działa prawidłowo, jeśli mapy już jest pusta.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCCollections#61](../../mfc/codesnippet/cpp/cmap-class_6.cpp)]  
  
##  <a name="removekey"></a>  CMap::RemoveKey  
 Wyszukuje wpisu mapy odpowiadający podany klucz; następnie Jeśli klucz zostanie znaleziony, usuwa wpis.  
  
```  
BOOL RemoveKey(ARG_KEY key);
```  
  
### <a name="parameters"></a>Parametry  
 `ARG_KEY`  
 Parametr szablonu określający typ klucza.  
  
 `key`  
 Klucz elementu do usunięcia.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli wpis został znaleziony i pomyślnie usunął; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 **Destructelements —** funkcji Pomocnik służy do usuwania wpis.  
  
### <a name="example"></a>Przykład  
 Zobacz przykład [CMap::SetAt](#setat).  
  
##  <a name="setat"></a>  CMap::SetAt  
 Podstawowy oznacza, że wstawić element na mapie.  
  
```  
void SetAt(ARG_KEY key, ARG_VALUE newValue);
```  
  
### <a name="parameters"></a>Parametry  
 `ARG_KEY`  
 Określenie typu parametru szablonu `key` parametru.  
  
 `key`  
 Określa klucz nowego elementu.  
  
 `ARG_VALUE`  
 Określenie typu parametru szablonu `newValue` parametru.  
  
 `newValue`  
 Określa wartość nowego elementu.  
  
### <a name="remarks"></a>Uwagi  
 Po pierwsze wyszukiwania klucza. Jeśli klucz zostanie znaleziony, a następnie zostanie zmieniona wartość odpowiadająca; w przeciwnym razie utworzono nową parę klucz wartość.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCCollections#62](../../mfc/codesnippet/cpp/cmap-class_7.cpp)]  
  
## <a name="see-also"></a>Zobacz też  
 [Przykładowe MFC ZBIERANIE](../../visual-cpp-samples.md)   
 [CObject — klasa](../../mfc/reference/cobject-class.md)   
 [Wykres hierarchii](../../mfc/hierarchy-chart.md)  
