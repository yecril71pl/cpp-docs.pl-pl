---
title: Klasa CStdioFile | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-windows
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- CStdioFile
- AFX/CStdioFile
- AFX/CStdioFile::CStdioFile
- AFX/CStdioFile::Open
- AFX/CStdioFile::ReadString
- AFX/CStdioFile::Seek
- AFX/CStdioFile::WriteString
- AFX/CStdioFile::m_pStream
dev_langs:
- C++
helpviewer_keywords:
- CStdioFile [MFC], CStdioFile
- CStdioFile [MFC], Open
- CStdioFile [MFC], ReadString
- CStdioFile [MFC], Seek
- CStdioFile [MFC], WriteString
- CStdioFile [MFC], m_pStream
ms.assetid: 88c2274c-4f0e-4327-882a-557ba4b3ae15
caps.latest.revision: 22
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 868442a2936781ed24588f47dcb591cadcc48f0d
ms.sourcegitcommit: 0523c88b24d963c33af0529e6ba85ad2c6ee5afb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/10/2018
---
# <a name="cstdiofile-class"></a>Klasa CStdioFile
Reprezentuje plik strumienia środowiska wykonawczego C, jak otworzyć za pomocą funkcji środowiska wykonawczego [fopen —](../../c-runtime-library/reference/fopen-wfopen.md).  
  
## <a name="syntax"></a>Składnia  
  
```  
class CStdioFile : public CFile  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CStdioFile::CStdioFile](#cstdiofile)|Konstruuje `CStdioFile` obiektu ze wskaźnika ścieżki lub pliku.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CStdioFile::Open](#open)|Przeciążone. Otwórz jest przeznaczony do użytku z domyślnym `CStdioFile` — Konstruktor (zastępuje [CFile::Open](../../mfc/reference/cfile-class.md#open)).|  
|[CStdioFile::ReadString](#readstring)|Odczytuje pojedynczy wiersz tekstu.|  
|[CStdioFile::Seek](#seek)|Określa położenie bieżącego wskaźnika pliku.|  
|[CStdioFile::WriteString](#writestring)|Zapisuje pojedynczy wiersz tekstu.|  
  
### <a name="public-data-members"></a>Publiczne elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CStdioFile::m_pStream](#m_pstream)|Zawiera wskaźnik do otwartego pliku.|  
  
## <a name="remarks"></a>Uwagi  
 Przesyłanie strumieniowe plików są buforowane i można je otwierać w trybie tekstowym (ustawienie domyślne) lub w trybie binarnym.  
  
 Tryb tekstu zapewnia specjalnego przetwarzania dla pary wysuwu wiersza powrotu karetki. Podczas zapisu nowym wierszem znaków (0x0A) do trybu tekst `CStdioFile` obiektu, pary bajtów (0x0D, 0x0A) są wysyłane do pliku. Po przeczytaniu, pary bajtów (0x0D, 0x0A) są tłumaczone na jednobajtowe 0x0A.  
  
 [Cfile —](../../mfc/reference/cfile-class.md) funkcje [zduplikowane](../../mfc/reference/cfile-class.md#duplicate), [LockRange](../../mfc/reference/cfile-class.md#lockrange), i [UnlockRange](../../mfc/reference/cfile-class.md#unlockrange) nie są obsługiwane dla `CStdioFile`.  
  
 Jeśli wywoływać te funkcje na `CStdioFile`, otrzymasz [CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md).  
  
 Aby uzyskać więcej informacji na temat używania `CStdioFile`, zobacz artykuły [pliki w MFC](../../mfc/files-in-mfc.md) i [Obsługa plików](../../c-runtime-library/file-handling.md) w *odwołanie do biblioteki wykonawczej*.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CFile](../../mfc/reference/cfile-class.md)  
  
 `CStdioFile`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afx.h  
  
##  <a name="cstdiofile"></a>  CStdioFile::CStdioFile  
 Tworzy i inicjuje `CStdioFile` obiektu.  
  
```  
CStdioFile();  
CStdioFile(CAtlTransactionManager* pTM);  
  CStdioFile(FILE* pOpenStream);

 
CStdioFile(
    LPCTSTR lpszFileName,  
    UINT nOpenFlags);

 
CStdioFile(
    LPCTSTR lpszFileName,
    UINT nOpenFlags,
    CAtlTransactionManager* pTM);
```  
  
### <a name="parameters"></a>Parametry  
 `pOpenStream`  
 Określa wskaźnika pliku zwrócony przez wywołanie funkcji wykonawcze języka C [fopen —](../../c-runtime-library/reference/fopen-wfopen.md).  
  
 `lpszFileName`  
 Określa ciąg, który jest ścieżka do żądanego pliku. Ścieżka może być względna lub bezwzględna.  
  
 `nOpenFlags`  
 Określa opcje tworzenia pliku, udostępniania plików i tryby dostępu do pliku. Można określić wiele opcji przy użyciu wartości bitowe lub ( `|`) operatora.  
  
 W trybie jednego dostępu do pliku jest wymagana; inne sposoby są opcjonalne. Zobacz [CFile::CFile](../../mfc/reference/cfile-class.md#cfile) listę opcji trybu i inne flagi. W wersji 3.0 i nowszych MFC udziału flagi są dozwolone.  
  
 `pTM`  
 Wskaźnik do obiektu CAtlTransactionManager.  
  
### <a name="remarks"></a>Uwagi  
 Domyślny konstruktor nie dołączyć plik do `CStdioFile` obiektu. Podczas używania tego konstruktora, należy użyć `CStdioFile::Open` metody w celu otwarcia pliku i dołączenie go do `CStdioFile` obiektu.  
  
 Konstruktor jednym parametrem dołącza strumienia otwarty plik do `CStdioFile` obiektu. Dozwolone wartości wskaźnika zawierają wskaźniki wstępnie zdefiniowanych pliku wejścia/wyjścia `stdin`, `stdout`, lub `stderr`.  
  
 Tworzy konstruktora dwóch parametrów `CStdioFile` obiektu i otwiera odpowiedniego pliku z danej ścieżki.  
  
 W przypadku przekazania `NULL` dla dowolnego `pOpenStream` lub `lpszFileName`, zgłasza konstruktora `CInvalidArgException*`.  
  
 Jeśli pliku nie można otworzyć lub utworzyć, zgłasza konstruktora `CFileException*`.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCFiles#37](../../atl-mfc-shared/reference/codesnippet/cpp/cstdiofile-class_1.cpp)]  
  
##  <a name="m_pstream"></a>  CStdioFile::m_pStream  
 `m_pStream` Elementu członkowskiego danych jest wskaźnik do otwartego pliku, ponieważ zwracane przez funkcję wykonawcze języka C `fopen`.  
  
```  
FILE* m_pStream;  
```  
  
### <a name="remarks"></a>Uwagi  
 Jest **NULL** Jeśli plik nie został otwarty lub został zamknięty.  
  
##  <a name="open"></a>  CStdioFile::Open  
 Przeciążone. Otwórz jest przeznaczony do użytku z domyślnym `CStdioFile` konstruktora.  
  
```  
virtual BOOL Open(
    LPCTSTR lpszFileName,  
    UINT nOpenFlags,  
    CFileException* pError = NULL);

 
virtual BOOL Open(
    LPCTSTR lpszFileName,  
    UINT nOpenFlags,  
    CAtlTransactionManager* pTM,  
    CFileException* pError = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszFileName`  
 Ciąg, który jest ścieżka do żądanego pliku. Ścieżka może być względna lub bezwzględna.  
  
 `nOpenFlags`  
 Tryb dostępu i udostępniania. Określa akcję wykonywaną podczas otwierania pliku. Opcje można połączyć za pomocą wartości bitowe lub (&#124;) operatora. Opcji jednego udziału i uprawnień dostępu co są wymagane; tryby modeCreate i modeNoInherit są opcjonalne.  
  
 `pError`  
 Wskaźnik do istniejącego obiektu wyjątku plików, który zostanie wyświetlony stan operacji nie powiodło się.  
  
 `pTM`  
 Wskaźnik do `CAtlTransactionManager` obiektu.  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE` w przypadku powodzenia; w przeciwnym razie `FALSE`.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="readstring"></a>  CStdioFile::ReadString  
 Odczytuje dane tekstu w buforze, do limitu `nMax`-1, znaki z pliku skojarzone z `CStdioFile` obiektu.  
  
```  
virtual LPTSTR ReadString(
    LPTSTR lpsz,  
    UINT nMax);  
  
virtual BOOL ReadString(CString& rString);
```  
  
### <a name="parameters"></a>Parametry  
 `lpsz`  
 Określa wskaźnik do buforu dostarczone przez użytkownika, który będzie otrzymywał ciąg tekstowy zerem.  
  
 `nMax`  
 Określa maksymalną liczbę znaków do odczytu, nie licząc znak końcowy null.  
  
 `rString`  
 Odwołanie do `CString` obiekt, który będzie zawierać ciąg, gdy funkcja zwraca wartość.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do buforu, zawierający dane tekstowe. **Wartość NULL** jeśli osiągnięto koniec pliku przed odczytaniem żadnych danych; lub jeśli jest to wartość logiczna, **FALSE** czy osiągnięto koniec pliku przed odczytaniem żadnych danych.  
  
### <a name="remarks"></a>Uwagi  
 Odczytywanie została zatrzymana przez pierwszy znak nowego wiersza. Jeśli w tym przypadku mniej niż `nMax`odczytano wartość-1 znaków, znaków nowego wiersza są przechowywane w buforze. Znak null ('\0') jest dołączany w każdym przypadku.  
  
 [CFile::Read](../../mfc/reference/cfile-class.md#read) jest również dostępna dla danych wejściowych w trybie tekstowym, ale nie zakończy na parę wysuwu wiersza powrotu karetki.  
  
> [!NOTE]
>  `CString` Wersja ta funkcja usuwa `'\n'` Jeśli występuje; `LPTSTR` nie obsługuje wersji.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCFiles#38](../../atl-mfc-shared/reference/codesnippet/cpp/cstdiofile-class_2.cpp)]  
  
##  <a name="seek"></a>  CStdioFile::Seek  
 Zmienia położenie wskaźnika w wcześniej otwartych plików.  
  
```  
virtual ULONGLONG Seek(
    LONGLONG lOff,  
    UINT nFrom);
```  
  
### <a name="parameters"></a>Parametry  
 `lOff`  
 Liczba bajtów do wskaźnika.  
  
 `nFrom`  
 Tryb przesuwanie wskaźnika. Musi być jedną z następujących wartości:  
  
- `CFile::begin`: Wskaźnika pliku `lOff` bajtów w przód od początku pliku.  
  
- `CFile::current`: Wskaźnika pliku `lOff` bajtów z bieżącej pozycji w pliku.  
  
- `CFile::end`: Wskaźnika pliku `lOff` bajtów na końcu pliku. Należy pamiętać, że `lOff` musi być ujemna do wyszukania do istniejącego pliku; dodatnią wartości będzie wyszukiwać poza końcem pliku.  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli żądana pozycja jest dozwolony, `Seek` zwraca nowe przesunięcie bajtów od początku pliku. W przeciwnym razie wartość zwracana jest niezdefiniowane i `CFileException` obiekt jest generowany.  
  
### <a name="remarks"></a>Uwagi  
 `Seek` Funkcji zezwala na dostępie do zawartości pliku Przesuń wskaźnik określonym, absolutnie lub względnie. Nie są faktycznie odczytywane dane podczas wyszukiwania. Jeśli żądana pozycja jest większy niż rozmiar pliku, długość pliku będzie dotyczyć tej pozycji, a nie zostanie wygenerowany wyjątek.  
  
 Po otwarciu pliku wskaźnika pliku znajduje się w przesunięciu 0, początku pliku.  
  
 Ta implementacja `Seek` jest oparta na funkcji biblioteki czasu wykonywania (CRT) `fseek`. Istnieje kilka ograniczeń na użycie `Seek` na strumienie otwarty w trybie tekstowym. Aby uzyskać więcej informacji, zobacz [fseek, _fseeki64 —](../../c-runtime-library/reference/fseek-fseeki64.md).  
  
### <a name="example"></a>Przykład  
 Poniższy przykład przedstawia użycie `Seek` umieszczenie wskaźnika myszy 1000 bajtów od początku `cfile` pliku. Należy pamiętać, że `Seek` nie odczytuje danych, więc później należy wywołać [CStdioFile::ReadString](#readstring) można odczytać danych.  
  
 [!code-cpp[NVC_MFCFiles#39](../../atl-mfc-shared/reference/codesnippet/cpp/cstdiofile-class_3.cpp)]  
  
##  <a name="writestring"></a>  CStdioFile::WriteString  
 Zapisuje dane z bufora do pliku związanego z `CStdioFile` obiektu.  
  
```  
virtual void WriteString(LPCTSTR lpsz);
```  
  
### <a name="parameters"></a>Parametry  
 `lpsz`  
 Określa wskaźnik do buforu, który zawiera ciąg znaków zakończony znakiem null.  
  
### <a name="remarks"></a>Uwagi  
 Znak końcowy null ( `\0`) nie są zapisywane do pliku. Ta metoda zapisuje znaki nowego wiersza `lpsz` do pliku jako para powrotu/wysuw wiersza karetki.  
  
 Jeśli chcesz zapisać dane, które nie jest zerem do pliku, użyj `CStdioFile::Write` lub [CFile::Write](../../mfc/reference/cfile-class.md#write).  
  
 Ta metoda zgłasza `CInvalidArgException*` Jeśli określisz `NULL` dla `lpsz` parametru.  
  
 Ta metoda zgłasza `CFileException*` w odpowiedzi na błędy systemu plików.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCFiles#40](../../atl-mfc-shared/reference/codesnippet/cpp/cstdiofile-class_4.cpp)]  
  
## <a name="see-also"></a>Zobacz też  
 [Cfile — klasa](../../mfc/reference/cfile-class.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Cfile — klasa](../../mfc/reference/cfile-class.md)   
 [CFile::Duplicate](../../mfc/reference/cfile-class.md#duplicate)   
 [CFile::LockRange](../../mfc/reference/cfile-class.md#lockrange)   
 [CFile::UnlockRange](../../mfc/reference/cfile-class.md#unlockrange)   
 [Klasa CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md)
