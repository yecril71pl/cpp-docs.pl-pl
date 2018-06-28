---
title: Klasa CMemFile | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMemFile
- AFX/CMemFile
- AFX/CMemFile::CMemFile
- AFX/CMemFile::Attach
- AFX/CMemFile::Detach
- AFX/CMemFile::Alloc
- AFX/CMemFile::Free
- AFX/CMemFile::GrowFile
- AFX/CMemFile::Memcpy
- AFX/CMemFile::Realloc
dev_langs:
- C++
helpviewer_keywords:
- CMemFile [MFC], CMemFile
- CMemFile [MFC], Attach
- CMemFile [MFC], Detach
- CMemFile [MFC], Alloc
- CMemFile [MFC], Free
- CMemFile [MFC], GrowFile
- CMemFile [MFC], Memcpy
- CMemFile [MFC], Realloc
ms.assetid: 20e86515-e465-4f73-b2ea-e49789d63165
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e13c3b609a53e8c885e04530995a11218bf2704d
ms.sourcegitcommit: f1b051abb1de3fe96350be0563aaf4e960da13c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/27/2018
ms.locfileid: "37040067"
---
# <a name="cmemfile-class"></a>Klasa CMemFile
[Cfile —](../../mfc/reference/cfile-class.md)-klasy, który obsługuje pliki pamięci.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CMemFile : public CFile  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CMemFile::CMemFile](#cmemfile)|Tworzy obiekt pliku pamięci.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CMemFile::Attach](#attach)|Dołącza blok pamięci, aby `CMemFile`.|  
|[CMemFile::Detach](#detach)|Odłącza blok pamięci od `CMemFile` i zwraca wskaźnik do bloku pamięci odłączone.|  
  
### <a name="protected-methods"></a>Metody chronione  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CMemFile::Alloc](#alloc)|Należy przesłonić, aby zmodyfikować zachowanie alokacji pamięci.|  
|[CMemFile::Free](#free)|Należy przesłonić, aby zmodyfikować zachowanie cofania alokacji pamięci.|  
|[CMemFile::GrowFile](#growfile)|Należy przesłonić, aby zmodyfikować zachowanie podczas powiększania pliku.|  
|[CMemFile::Memcpy](#memcpy)|Należy przesłonić, aby zmodyfikować zachowanie kopii pamięci podczas odczytywania i zapisywania plików.|  
|[CMemFile::Realloc](#realloc)|Należy przesłonić, aby zmodyfikować zachowanie; Ponowna alokacja pamięci.|  
  
## <a name="remarks"></a>Uwagi  
 Te pliki pamięci przypominają plików na dysku, z wyjątkiem tego, że plik jest przechowywany w pamięci RAM, a nie na dysku. Pliku pamięci jest przydatne do szybkiego tymczasowego przechowywania lub przesyłania bajtów raw lub serializować obiektów między procesami niezależne.  
  
 `CMemFile` obiekty automatycznie można przydzielić pamięci własnych lub można dołączać własne bloku pamięci `CMemFile` obiektu przez wywołanie metody [Attach](#attach). W obu przypadkach jest przydzielana pamięć dla automatycznie powiększania pliku pamięci w `nGrowBytes`-o rozmiarze zwiększa, jeśli `nGrowBytes` nie jest równa zero.  
  
 Blok pamięci zostanie automatycznie usunięte podczas niszczenia `CMemFile` obiektu, jeśli pamięć pierwotnie został przydzielony przez `CMemFile` obiektu; w przeciwnym razie jest odpowiedzialny za dealokowanie pamięci dołączony do obiektu.  
  
 Dostęp do bloku pamięci za pomocą wskaźnika dostarczana, gdy zostanie odłączona od `CMemFile` obiektu przez wywołanie metody [Detach](#detach).  
  
 Najczęściej używane `CMemFile` jest utworzenie `CMemFile` obiektów i przy jego użyciu, wywołując [cfile —](../../mfc/reference/cfile-class.md) funkcji elementów członkowskich. Należy pamiętać, że tworzenie `CMemFile` automatycznie otwiera: Nie wywołuj [CFile::Open](../../mfc/reference/cfile-class.md#open), które służy tylko do plików na dysku. Ponieważ `CMemFile` nie używa pliku dysku, element członkowski danych `CFile::m_hFile` nie jest używany.  
  
 `CFile` Funkcje Członkowskie [zduplikowane](../../mfc/reference/cfile-class.md#duplicate), [LockRange](../../mfc/reference/cfile-class.md#lockrange), i [UnlockRange](../../mfc/reference/cfile-class.md#unlockrange) nie są zaimplementowane w przypadku `CMemFile`. Jeśli wywoływać te funkcje na `CMemFile` obiektu, otrzymasz [CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md).  
  
 `CMemFile` używa funkcji biblioteki wykonawczej [— funkcja malloc](../../c-runtime-library/reference/malloc.md), [realloc](../../c-runtime-library/reference/realloc.md), i [wolnego](../../c-runtime-library/reference/free.md) przydzielić, Przydziel ponownie, i cofnięcia przydzielenia pamięci; i wewnętrzne [memcpy](../../c-runtime-library/reference/memcpy-wmemcpy.md) w bloku Kopia pamięci podczas odczytywania i zapisywania. Jeśli chcesz zmienić to zachowanie lub zachowania podczas `CMemFile` rozwoju pliku, pochodzi z klasy z `CMemFile` i zastąpić odpowiednie funkcje.  
  
 Aby uzyskać więcej informacji na temat `CMemFile`, zobacz artykuły [pliki w MFC](../../mfc/files-in-mfc.md) i [zarządzania pamięci (MFC)](../../mfc/memory-management.md) i zobacz [Obsługa plików](../../c-runtime-library/file-handling.md) w *środowiska wykonawczego Odwołanie do biblioteki*.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [Cfile —](../../mfc/reference/cfile-class.md)  
  
 `CMemFile`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afx.h  
  
##  <a name="alloc"></a>  CMemFile::Alloc  
 Ta funkcja jest wywoływana `CMemFile` funkcji elementów członkowskich.  
  
```  
virtual BYTE* Alloc(SIZE_T nBytes);
```  
  
### <a name="parameters"></a>Parametry  
 *nBytes*  
 Liczba bajtów pamięci do przydzielenia.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do bloku pamięci, która została przydzielona lub **NULL** przypadku alokacja nie powiodło się.  
  
### <a name="remarks"></a>Uwagi  
 Zastąpienie tej funkcji do zaimplementowania alokacji pamięci niestandardowych. Jeśli przesłonić tę funkcję, prawdopodobnie należy do przesłonięcia [wolne](#free) i [Realloc](#realloc) również.  
  
 Domyślna implementacja używa funkcji biblioteki wykonawczej [— funkcja malloc](../../c-runtime-library/reference/malloc.md) można przydzielić pamięci.  
  
##  <a name="attach"></a>  CMemFile::Attach  
 Wywołanie tej funkcji, aby dołączyć blok pamięci, aby `CMemFile`.  
  
```  
void Attach(
    BYTE* lpBuffer,  
    UINT nBufferSize,  
    UINT nGrowBytes = 0);
```  
  
### <a name="parameters"></a>Parametry  
 *Sprawdzanie*  
 Wskaźnik do buforu, który jest dołączony do `CMemFile`.  
  
 *nBufferSize*  
 Liczba całkowita określająca rozmiar bufora w bajtach.  
  
 *nGrowBytes*  
 Przyrost alokacji pamięci w bajtach.  
  
### <a name="remarks"></a>Uwagi  
 Powoduje to `CMemFile` do użycia jako plik pamięci bloku pamięci.  
  
 Jeśli *nGrowBytes* ma wartość 0, `CMemFile` ustawi długość pliku *nBufferSize*. Oznacza to, że dane w bloku pamięci przed został dołączony do `CMemFile` będzie służyć jako plik. Nie można zwiększyć pamięci plików utworzonych w ten sposób.  
  
 Ponieważ plik nie może być parametrach wymaganych, należy uważać, aby nie spowodować `CMemFile` prób powiększania pliku. Na przykład nie wywołuj `CMemFile` zastąpień o [CFile:Write](../../mfc/reference/cfile-class.md#write) do zapisu poza końcem lub Nie wywołuj [CFile:SetLength](../../mfc/reference/cfile-class.md#setlength) o długości ponad *nBufferSize*.  
  
 Jeśli *nGrowBytes* jest większa niż 0, `CMemFile` zignoruje zawartości bloku pamięci jest podłączona. Będzie konieczne zapisanie zawartości pliku pamięci od podstaw przy użyciu `CMemFile` zastąpienie `CFile::Write`. Próba zapisu poza końcem pliku lub rozszerzenie pliku przez wywołanie metody `CMemFile` zastąpienie `CFile::SetLength`, `CMemFile` wzrośnie alokacji pamięci w przyrostach *nGrowBytes*. Rośnie alokacji pamięci zakończy się niepowodzeniem, jeśli blok pamięci, należy przekazać do `Attach` nie zostało przydzielone za pomocą metody, które są zgodne z [alokacji](#alloc). Aby był zgodny z domyślną implementację elementu `Alloc`, należy przydzielić pamięci za pomocą funkcji biblioteki wykonawczej [— funkcja malloc](../../c-runtime-library/reference/malloc.md) lub [calloc —](../../c-runtime-library/reference/calloc.md).  
  
##  <a name="cmemfile"></a>  CMemFile::CMemFile  
 Pierwszy przeciążenia otwiera plik pusty pamięci.  
  
```  
CMemFile(UINT nGrowBytes = 1024);

 
CMemFile(
    BYTE* lpBuffer,  
    UINT nBufferSize,  
    UINT nGrowBytes = 0);
```  
  
### <a name="parameters"></a>Parametry  
 *nGrowBytes*  
 Przyrost alokacji pamięci w bajtach.  
  
 *lpBuffe*r  
 Wskaźnik do buforu, który odbiera informacje o rozmiarze *nBufferSize*.  
  
 *nBufferSize*  
 Liczba całkowita określająca rozmiar bufora pliku w bajtach.  
  
### <a name="remarks"></a>Uwagi  
 Należy pamiętać, że plik jest otwarty przez konstruktora i że nie należy wywołania [CFile::Open](../../mfc/reference/cfile-class.md#open).  
  
 Przeciążenie drugi działa, takie same tak, jakby używane pierwszy Konstruktor i natychmiast o nazwie [Attach](#attach) z takimi samymi parametrami. Zobacz `Attach` szczegółowe informacje.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCFiles#36](../../atl-mfc-shared/reference/codesnippet/cpp/cmemfile-class_1.cpp)]  
  
##  <a name="detach"></a>  CMemFile::Detach  
 Wywołanie tej funkcji, otrzymywać wskaźnik do bloku pamięci używane przez `CMemFile`.  
  
```  
BYTE* Detach();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do bloku pamięci, która zawiera zawartość pliku pamięci.  
  
### <a name="remarks"></a>Uwagi  
 Wywołanie tej funkcji również zamyka `CMemFile`. Można ponownie dołączyć bloku pamięci `CMemFile` przez wywołanie metody [Attach](#attach). Jeśli chcesz ponownie dołączyć plik i korzystanie z danych, należy wywołać [CFile::GetLength](../../mfc/reference/cfile-class.md#getlength) uzyskać długość pliku przed wywołaniem `Detach`. Należy pamiętać, że po dołączeniu bloku pamięci `CMemFile` , aby mogli używać swoich danych ( `nGrowBytes` == 0), a następnie nie będzie można powiększać pliku pamięci.  
  
##  <a name="free"></a>  CMemFile::Free  
 Ta funkcja jest wywoływana `CMemFile` funkcji elementów członkowskich.  
  
```  
virtual void Free(BYTE* lpMem);
```  
  
### <a name="parameters"></a>Parametry  
 *lpMem*  
 Wskaźnik do pamięci do przydzielenia.  
  
### <a name="remarks"></a>Uwagi  
 Zastąpienie tej funkcji do zaimplementowania dezalokacja pamięci niestandardowych. Jeśli przesłonić tę funkcję, prawdopodobnie należy do przesłonięcia [alokacji](#alloc) i [Realloc](#realloc) również.  
  
##  <a name="growfile"></a>  CMemFile::GrowFile  
 Ta funkcja jest wywoływana przez kilka `CMemFile` funkcji elementów członkowskich.  
  
```  
virtual void GrowFile(SIZE_T dwNewLen);
```  
  
### <a name="parameters"></a>Parametry  
 *dwNewLen*  
 Nowy rozmiar pliku pamięci.  
  
### <a name="remarks"></a>Uwagi  
 Można ją zastąpić, jeśli chcesz zmienić sposób `CMemFile` rozwoju jego pliku. Domyślna implementacja wywołuje [Realloc](#realloc) zwiększa istniejącego bloku (lub [alokacji](#alloc) do utworzenia bloku pamięci), przydzielania pamięci wielokrotności `nGrowBytes` wartość określona w konstruktorze lub [Attach](#attach) wywołania.  
  
##  <a name="memcpy"></a>  CMemFile::Memcpy  
 Ta funkcja jest wywoływana `CMemFile` zastąpień o [CFile::Read](../../mfc/reference/cfile-class.md#read) i [CFile::Write](../../mfc/reference/cfile-class.md#write) na przesyłanie danych do i z pliku pamięci.  
  
```  
virtual BYTE* Memcpy(
    BYTE* lpMemTarget,  
    const BYTE* lpMemSource,  
    SIZE_T nBytes);
```  
  
### <a name="parameters"></a>Parametry  
 *lpMemTarget*  
 Wskaźnik do bloku pamięci, do którego zostaną skopiowane pamięci źródła.  
  
 *lpMemSource*  
 Wskaźnik do bloku pamięci źródłowego.  
  
 *nBytes*  
 Liczba bajtów do skopiowania.  
  
### <a name="return-value"></a>Wartość zwracana  
 Kopię *lpMemTarget*.  
  
### <a name="remarks"></a>Uwagi  
 Zastąpienie tej funkcji, jeśli chcesz zmienić sposób który `CMemFile` jest te kopie pamięci.  
  
##  <a name="realloc"></a>  CMemFile::Realloc  
 Ta funkcja jest wywoływana `CMemFile` funkcji elementów członkowskich.  
  
```  
virtual BYTE* Realloc(
    BYTE* lpMem,  
    SIZE_T nBytes);
```  
  
### <a name="parameters"></a>Parametry  
 *lpMem*  
 Wskaźnik do bloku pamięci odbiorczego.  
  
 *nBytes*  
 Nowy rozmiar bloku pamięci.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do bloku pamięci przydzielić (i prawdopodobnie przeniesiona), lub **NULL** Jeśli ponowne przydzielenie nie powiodła się.  
  
### <a name="remarks"></a>Uwagi  
 Zastąpienie tej funkcji do zaimplementowania; Ponowna alokacja pamięci niestandardowych. Jeśli przesłonić tę funkcję, prawdopodobnie należy do przesłonięcia [alokacji](#alloc) i [wolne](#free) również.  
  
## <a name="see-also"></a>Zobacz też  
 [Cfile — klasa](../../mfc/reference/cfile-class.md)   
 [Wykres hierarchii](../../mfc/hierarchy-chart.md)



