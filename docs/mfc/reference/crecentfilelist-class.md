---
title: Klasa CRecentFileList
ms.date: 11/04/2016
f1_keywords:
- CRecentFileList
- AFXADV/CRecentFileList
- AFXADV/CRecentFileList::CRecentFileList
- AFXADV/CRecentFileList::Add
- AFXADV/CRecentFileList::GetDisplayName
- AFXADV/CRecentFileList::GetSize
- AFXADV/CRecentFileList::ReadList
- AFXADV/CRecentFileList::Remove
- AFXADV/CRecentFileList::UpdateMenu
- AFXADV/CRecentFileList::WriteList
helpviewer_keywords:
- CRecentFileList [MFC], CRecentFileList
- CRecentFileList [MFC], Add
- CRecentFileList [MFC], GetDisplayName
- CRecentFileList [MFC], GetSize
- CRecentFileList [MFC], ReadList
- CRecentFileList [MFC], Remove
- CRecentFileList [MFC], UpdateMenu
- CRecentFileList [MFC], WriteList
ms.assetid: a77f0524-7584-4582-849a-7e97b76d186e
ms.openlocfilehash: 30536d91d057de4e551b5a28200dd903e12713b3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62372182"
---
# <a name="crecentfilelist-class"></a>Klasa CRecentFileList

Obsługuje formant listy ostatnio używanych plików (MRU).

## <a name="syntax"></a>Składnia

```
class CRecentFileList
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CRecentFileList::CRecentFileList](#crecentfilelist)|Konstruuje `CRecentFileList` obiektu.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CRecentFileList::Add](#add)|Dodaje plik do listy ostatnio używanych plików.|
|[CRecentFileList::GetDisplayName](#getdisplayname)|Zawiera nazwę wyświetlaną dla wyświetlanie menu, nazwa_pliku MRU.|
|[CRecentFileList::GetSize](#getsize)|Pobiera liczbę plików na liście ostatnio używanych plików.|
|[CRecentFileList::ReadList](#readlist)|Odczytuje listy ostatnio używanych plików z rejestru lub. Pliku INI.|
|[CRecentFileList::Remove](#remove)|Usuwa plik z listy ostatnio używanych plików.|
|[CRecentFileList::UpdateMenu](#updatemenu)|Aktualizuje wyświetlanie menu listy ostatnio używanych plików.|
|[CRecentFileList::WriteList](#writelist)|Zapisuje listy ostatnio używanych plików z rejestru lub. Pliku INI.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CRecentFileList::operator \[ \]](#operator_at)|Zwraca `CString` obiekt na określonej pozycji.|

## <a name="remarks"></a>Uwagi

Pliki mogą być dodawane do lub usunięte z listy ostatnio używanych plików, lista plików może być odczytywany lub zapisywane w rejestrze lub. Można zaktualizować pliku INI i menu, wyświetlanie listy ostatnio używanych plików.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`CRecentFileList`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxadv.h

##  <a name="add"></a>  CRecentFileList::Add

Dodaje plik do listy ostatnio używanych plików (MRU).

```
virtual void Add(LPCTSTR lpszPathName);

virtual void Add(
    LPCTSTR lpszPathName,
    LPCTSTR lpszAppID);

void Add(
    IShellItem* pItem,
    LPCTSTR lpszAppID);

void Add(
    IShellLink* pLink,
    LPCTSTR lpszAppID);

void Add(
    PIDLIST_ABSOLUTE pidl,
    LPCTSTR lpszAppID);
```

### <a name="parameters"></a>Parametry

*lpszPathName*<br/>
Określa nazwę ścieżki do dodania do listy.

*lpszAppID*<br/>
Określa identyfikator modelu użytkownika aplikacji dla aplikacji.

*pItem*<br/>
Określa wskaźnik do elementu powłoki do dodania do listy.

*pLink*<br/>
Określa wskaźnik linku powłoki, które mają zostać dodane do listy.

*PIDL*<br/>
Określa IDLIST dla elementu powłoki, na który powinny zostać dodane do folderu ostatnie docs.

### <a name="remarks"></a>Uwagi

Nazwa pliku zostanie dodany na początku listy ostatnio używanych. Jeśli nazwa pliku już istnieje na liście MRU, zostaną przeniesione do góry.

##  <a name="crecentfilelist"></a>  CRecentFileList::CRecentFileList

Konstruuje `CRecentFileList` obiektu.

```
CRecentFileList(
    UINT nStart,
    LPCTSTR lpszSection,
    LPCTSTR lpszEntryFormat,
    int nSize,
    int nMaxDispLen = AFX_ABBREV_FILENAME_LEN);
```

### <a name="parameters"></a>Parametry

*nStart*<br/>
Przesunięcie numerowania na wyświetlaczu menu (ostatnio używanych) pliku listy.

*lpszSection*<br/>
Wskazuje nazwę sekcji rejestru lub w aplikacji. Plik INI, gdzie odczytać lub zapisywane listy ostatnio używanych plików.

*lpszEntryFormat*<br/>
Wskazuje ciąg formatu, który ma być używany dla nazwy wpisów, przechowywane w rejestrze lub w aplikacji. Pliku INI.

*nSize*<br/>
Maksymalna liczba plików na liście ostatnio używanych plików.

*nMaxDispLen*<br/>
Maksymalna długość w znakach wyświetli menu nazwy pliku na liście ostatnio używanych plików.

### <a name="remarks"></a>Uwagi

Ciąg formatu, wskazywana przez *lpszEntryFormat* powinien zawierać "%d", który będzie używany dla podstawianie indeks każdego elementu listy ostatnio używanych. Na przykład, jeśli ciąg formatu jest `"file%d"` , a następnie będą miały nazwę nadaną wpisy `file0`, `file1`i tak dalej.

##  <a name="getdisplayname"></a>  CRecentFileList::GetDisplayName

Pobiera nazwę wyświetlaną dla pliku na liście ostatnio używanych plików do użytku w wyświetlanie menu listy ostatnio używanych elementów.

```
virtual BOOL GetDisplayName(
    CString& strName,
    int nIndex,
    LPCTSTR lpszCurDir,
    int nCurDir,
    BOOL bAtLeastName = TRUE) const;
```

### <a name="parameters"></a>Parametry

*strName*<br/>
Pełna ścieżka pliku, którego nazwa ma być wyświetlana na liście menu ostatnio używanych plików.

*nIndex*<br/>
Liczony od zera indeks pliku na liście ostatnio używanych plików.

*lpszCurDir*<br/>
Ciąg zawierający bieżącego katalogu.

*nCurDir*<br/>
Długość ciąg bieżącego katalogu.

*bAtLeastName*<br/>
Jeśli wartość jest niezerowa, wskazuje, czy nazwa podstawowa pliku ma zostać zwrócone, nawet jeśli przekracza długość maksymalna wyświetlana (przekazany jako *nMaxDispLen* parametr `CRecentFileList` konstruktora).

### <a name="return-value"></a>Wartość zwracana

**FALSE** czy nazwa pliku nie pod określonym indeksem na liście ostatnio używanych plików (MRU).

### <a name="remarks"></a>Uwagi

Jeśli plik znajduje się w bieżącym katalogu, funkcja pozostawia katalogu wyłączyć ekran. Jeśli nazwa pliku jest zbyt długa, katalogów i rozszerzenia są odrzucane. Jeśli nazwa pliku nadal jest zbyt długa, nazwę wyświetlaną jest ustawiony na pusty ciąg, chyba że *bAtLeastName* jest różna od zera.

##  <a name="getsize"></a>  CRecentFileList::GetSize

Pobiera liczbę plików na liście ostatnio używanych plików.

```
int GetSize() const;
```

### <a name="return-value"></a>Wartość zwracana

Liczba plików w bieżącym ostatnio używane listy plików (MRU).

##  <a name="operator_at"></a>  [] CRecentFileList::operator

Przeciążona indeksu dolnego (`[]`) — operator zwraca pojedynczą `CString` określony przez liczony od zera indeks w *nIndex*.

```
CString& operator[ ](int nindex);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Liczony od zera indeks `CString` w zestawie `CString`s.

##  <a name="readlist"></a>  CRecentFileList::ReadList

Odczytuje listy ostatnio używanych (MRU) pliku z rejestru lub aplikacji. Pliku INI.

```
virtual void ReadList();
```

##  <a name="remove"></a>  CRecentFileList::Remove

Usuwa plik z listy ostatnio używanych plików.

```
virtual void Remove(int nIndex);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Liczony od zera indeks pliku do usunięcia z listy ostatnio używanych plików (MRU).

##  <a name="updatemenu"></a>  CRecentFileList::UpdateMenu

Aktualizuje wyświetlanie menu listy ostatnio używanych plików.

```
virtual void UpdateMenu(CCmdUI* pCmdUI);
```

### <a name="parameters"></a>Parametry

*pCmdUI*<br/>
Wskaźnik do [CCmdUI](../../mfc/reference/ccmdui-class.md) obiekt menu listy ostatnio używanych plików (MRU).

##  <a name="writelist"></a>  CRecentFileList::WriteList

Zapisuje listy ostatnio używanych (MRU) pliku do rejestru lub w aplikacji. Pliku INI.

```
virtual void WriteList();
```

## <a name="see-also"></a>Zobacz także

[Wykres hierarchii](../../mfc/hierarchy-chart.md)
