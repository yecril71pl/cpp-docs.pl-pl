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
ms.openlocfilehash: a2102c6a39c14c548828e57ad1c49de6a5bc03dd
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370895"
---
# <a name="crecentfilelist-class"></a>Klasa CRecentFileList

Obsługuje kontrolę nad listą ostatnio używanych plików (MRU).

## <a name="syntax"></a>Składnia

```
class CRecentFileList
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Lista plików CRecent::CRecentFileList](#crecentfilelist)|Konstruuje `CRecentFileList` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Lista plików CRecent::Dodaj](#add)|Dodaje plik do listy plików MRU.|
|[Lista plików CRecent::GetDisplayName](#getdisplayname)|Udostępnia nazwę wyświetlaną dla wyświetlania menu nazwy pliku MRU.|
|[Lista plików CRecent::GetSize](#getsize)|Pobiera liczbę plików na liście plików MRU.|
|[CRecentFileList::Lista odczytu](#readlist)|Odczytuje listę plików MRU z rejestru lub . ini.|
|[Lista plików CRecent::Usuń](#remove)|Usuwa plik z listy plików MRU.|
|[Lista plików CRecent::AktualizacjaMenu](#updatemenu)|Aktualizuje wyświetlanie menu listy plików MRU.|
|[CRecentFileList::WriteList](#writelist)|Zapisuje listę plików MRU z rejestru lub . ini.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CRecentFileList::operator \[\]](#operator_at)|Zwraca `CString` obiekt w danej pozycji.|

## <a name="remarks"></a>Uwagi

Pliki można dodawać lub usuwać z listy plików MRU, lista plików może być odczytywana z rejestru lub zapisywana w rejestrze lub . ini, a menu z listą plików MRU można zaktualizować.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`CRecentFileList`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxadv.h

## <a name="crecentfilelistadd"></a><a name="add"></a>Lista plików CRecent::Dodaj

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

*lpszPathName (nazwa lpszPathName)*<br/>
Określa nazwa ścieżki, która ma zostać dodana do listy.

*lpszAppID*<br/>
Określa identyfikator modelu użytkownika aplikacji.

*pItem (własówce)*<br/>
Określa wskaźnik do elementu powłoki, który ma zostać dodany do listy.

*Plink*<br/>
Określa wskaźnik do łącza powłoki, który ma zostać dodany do listy.

*pidl*<br/>
Określa listę identyfikatorów elementu powłoki, który powinien zostać dodany do folderu ostatnich dokumentów.

### <a name="remarks"></a>Uwagi

Nazwa pliku zostanie dodana do górnej części listy MRU. Jeśli nazwa pliku już istnieje na liście MRU, zostanie przeniesiona na górę.

## <a name="crecentfilelistcrecentfilelist"></a><a name="crecentfilelist"></a>Lista plików CRecent::CRecentFileList

Konstruuje `CRecentFileList` obiekt.

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
Przesunięcie numeracji na ekranie menu listy plików MRU (ostatnio używane).

*lpszSekcja*<br/>
Wskazuje nazwę sekcji rejestru lub aplikacji . plik INI, w którym lista plików MRU jest odczytywana i/lub zapisywana.

*lpszEntryFormat*<br/>
Wskazuje ciąg formatu, który ma być używany dla nazw wpisów przechowywanych w rejestrze lub aplikacji . ini.

*nSize (rozmiar)*<br/>
Maksymalna liczba plików na liście plików MRU.

*nMaxDispLen*<br/>
Maksymalna długość w znakach dostępna dla wyświetlania menu nazwy pliku na liście plików MRU.

### <a name="remarks"></a>Uwagi

Ciąg formatu wskazany przez *lpszEntryFormat* powinien zawierać "%d", który będzie używany do zastępowania indeksu każdego elementu MRU. Na przykład, jeśli ciąg `"file%d"` formatu jest następnie `file0` `file1`wpisy zostaną nazwane , i tak dalej.

## <a name="crecentfilelistgetdisplayname"></a><a name="getdisplayname"></a>Lista plików CRecent::GetDisplayName

Uzyskuje nazwę wyświetlaną pliku na liście plików MRU do wykorzystania w menu listy MRU.

```
virtual BOOL GetDisplayName(
    CString& strName,
    int nIndex,
    LPCTSTR lpszCurDir,
    int nCurDir,
    BOOL bAtLeastName = TRUE) const;
```

### <a name="parameters"></a>Parametry

*nazwa strName*<br/>
Pełna ścieżka pliku, którego nazwa ma być wyświetlana na liście menu plików MRU.

*Nindex*<br/>
Indeks pliku opartego na wartości zerowej na liście plików MRU.

*lpszCurDir (lpszCurDir)*<br/>
Ciąg przytrzymując bieżący katalog.

*nCurDir ( nCurDir )*<br/>
Długość bieżącego ciągu katalogu.

*bAtLeastName*<br/>
Jeśli niezerowe, wskazuje, że nazwa podstawowa pliku powinny być zwracane, nawet jeśli przekracza maksymalną długość wyświetlania (przekazywane jako *parametr nMaxDispLen* do `CRecentFileList` konstruktora).

### <a name="return-value"></a>Wartość zwracana

**FALSE,** jeśli nie ma nazwy pliku w określonym indeksie na liście ostatnio używanych plików (MRU).

### <a name="remarks"></a>Uwagi

Jeśli plik znajduje się w bieżącym katalogu, funkcja pozostawia katalog poza ekranem. Jeśli nazwa pliku jest zbyt długa, katalog i rozszerzenie zostaną usunięte. Jeśli nazwa pliku jest nadal zbyt długa, nazwa wyświetlana jest ustawiona na pusty ciąg, chyba że *bAtLeastName* jest różna od zera.

## <a name="crecentfilelistgetsize"></a><a name="getsize"></a>Lista plików CRecent::GetSize

Pobiera liczbę plików na liście plików MRU.

```
int GetSize() const;
```

### <a name="return-value"></a>Wartość zwracana

Liczba plików na liście plików ostatnio używanych (MRU).

## <a name="crecentfilelistoperator--"></a><a name="operator_at"></a>CRecentFileList::operator [ ]

Przeciążony indeks dolny`[]`( ) `CString` zwraca pojedynczy określony przez indeks od zera w *nIndex*.

```
CString& operator[ ](int nindex);
```

### <a name="parameters"></a>Parametry

*Nindex*<br/>
Indeks od zera `CString` a w `CString`zestawie s.

## <a name="crecentfilelistreadlist"></a><a name="readlist"></a>CRecentFileList::Lista odczytu

Odczytuje listę ostatnio używanych plików (MRU) z rejestru lub aplikacji . ini.

```
virtual void ReadList();
```

## <a name="crecentfilelistremove"></a><a name="remove"></a>Lista plików CRecent::Usuń

Usuwa plik z listy plików MRU.

```
virtual void Remove(int nIndex);
```

### <a name="parameters"></a>Parametry

*Nindex*<br/>
Indeks oparty na wartości zerowej pliku, który ma zostać usunięty z listy ostatnio używanych plików (MRU).

## <a name="crecentfilelistupdatemenu"></a><a name="updatemenu"></a>Lista plików CRecent::AktualizacjaMenu

Aktualizuje wyświetlanie menu listy plików MRU.

```
virtual void UpdateMenu(CCmdUI* pCmdUI);
```

### <a name="parameters"></a>Parametry

*pCmdUI*<br/>
Wskaźnik do obiektu [CCmdUI](../../mfc/reference/ccmdui-class.md) dla ostatnio używanego menu listy plików (MRU).

## <a name="crecentfilelistwritelist"></a><a name="writelist"></a>CRecentFileList::WriteList

Zapisuje listę ostatnio używanych plików (MRU) do rejestru lub aplikacji . ini.

```
virtual void WriteList();
```

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)
