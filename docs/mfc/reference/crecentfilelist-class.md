---
title: Klasa CRecentFileList | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
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
dev_langs: C++
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
caps.latest.revision: "19"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 968c15b1382233dc166a174e4ef074033c76619c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="crecentfilelist-class"></a>Klasa CRecentFileList
Formant obsługuje listy ostatnio używanych (MRU) pliku.  
  
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
|[CRecentFileList::GetDisplayName](#getdisplayname)|Zawiera nazwę wyświetlaną dla wyświetlanie menu filename MRU.|  
|[CRecentFileList::GetSize](#getsize)|Pobiera liczbę plików na liście MRU.|  
|[CRecentFileList::ReadList](#readlist)|Odczytuje listę ostatnio używanych plików z rejestru lub. Pliku INI.|  
|[CRecentFileList::Remove](#remove)|Usuwa plik z listy ostatnio używanych plików.|  
|[CRecentFileList::UpdateMenu](#updatemenu)|Aktualizuje wyświetlanie menu listy ostatnio używanych plików.|  
|[CRecentFileList::WriteList](#writelist)|Zapisuje listy ostatnio używanych plików z rejestru lub. Pliku INI.|  
  
### <a name="public-operators"></a>Operatory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[[CRecentFileList::operator]](#operator_at)|Zwraca `CString` obiekt na określonej pozycji.|  
  
## <a name="remarks"></a>Uwagi  
 Pliki można dodawać lub usunięty z listy ostatnio używanych plików, listy plików może być zapisu lub odczytu z rejestru lub. Można zaktualizować pliku INI i menu Wyświetlanie listy ostatnio używanych plików.  
  
 Aby uzyskać więcej informacji o ostatnio używanych elementów menu zobacz  
  
-   Artykuł bazy wiedzy Q243751: Porada: Dodawanie programy obsługi poleceń dla ostatnio używanych elementów Menu w aplikacji MFC  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `CRecentFileList`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxadv.h  
  
##  <a name="add"></a>CRecentFileList::Add  
 Dodaje plik do listy plików ostatnio używanych (MRU).  
  
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
 `lpszPathName`  
 Określa nazwę ścieżki do dodania do listy.  
  
 `lpszAppID`  
 Określa identyfikator modelu użytkownika aplikacji dla aplikacji.  
  
 `pItem`  
 Określa wskaźnik do elementu powłoki mają zostać dodane do listy.  
  
 `pLink`  
 Określa wskaźnik do łącza powłoki mają zostać dodane do listy.  
  
 `pidl`  
 Określa IDLIST dla elementu powłoki, który powinien zostać dodany do ostatnie folderu dokumenty.  
  
### <a name="remarks"></a>Uwagi  
 Nazwa pliku zostanie dodany na początku listy. Jeśli nazwa pliku już istnieje na liście MRU, zostanie przeniesiony do góry.  
  
##  <a name="crecentfilelist"></a>CRecentFileList::CRecentFileList  
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
 `nStart`  
 Przesunięcie numerowania w menu Wyświetlanie listy plików MRU (ostatnio używane).  
  
 `lpszSection`  
 Wskazuje nazwę sekcji rejestru lub aplikacji. Plik INI, gdzie odczytu lub zapisywane listy ostatnio używanych plików.  
  
 `lpszEntryFormat`  
 Wskazuje ciąg formatu służący do nazwy wpisów przechowywane w rejestrze lub w aplikacji. Pliku INI.  
  
 `nSize`  
 Maksymalna liczba plików na liście MRU.  
  
 `nMaxDispLen`  
 Maksymalna długość w znakach do wyświetlenia menu nazwy pliku na liście ostatnio używanych plików.  
  
### <a name="remarks"></a>Uwagi  
 Ciąg formatu wskazywana przez `lpszEntryFormat` powinien zawierać "%d", która będzie używana dla podstawiając indeks każdego elementu MRU. Na przykład, jeśli ciąg formatu `"file%d"` , a następnie będzie miała nazwę wpisy `file0`, `file1`i tak dalej.  
  
##  <a name="getdisplayname"></a>CRecentFileList::GetDisplayName  
 Pobiera nazwę wyświetlaną dla pliku na liście ostatnio używanych plików do użytku w menu Wyświetlanie listy ostatnio używanych.  
  
```  
virtual BOOL GetDisplayName(
    CString& strName,  
    int nIndex,  
    LPCTSTR lpszCurDir,  
    int nCurDir,  
    BOOL bAtLeastName = TRUE) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `strName`  
 Pełna ścieżka pliku, którego nazwa ma być wyświetlany w menu listy ostatnio używanych plików.  
  
 `nIndex`  
 Liczony od zera indeks pliku na liście ostatnio używanych plików.  
  
 *lpszCurDir*  
 Ciąg zawierający bieżącego katalogu.  
  
 *nCurDir*  
 Długość ciągu bieżącego katalogu.  
  
 `bAtLeastName`  
 Jeśli różną od zera, wskazuje, że podstawowa nazwa pliku ma zostać zwrócony, nawet jeśli jego rozmiar przekracza długość maksymalną wyświetlania (przekazany jako `nMaxDispLen` parametr `CRecentFileList` konstruktora).  
  
### <a name="return-value"></a>Wartość zwracana  
 **FALSE** Jeśli istnieje żadnej nazwy pliku od określonego indeksu na liście plików ostatnio używanych (MRU).  
  
### <a name="remarks"></a>Uwagi  
 Jeśli plik znajduje się w bieżącym katalogu, funkcja pozostawia katalogu opcję wyświetlania. Jeśli nazwa pliku jest za długa, katalogów i rozszerzenia są usuwane. Jeśli nazwa pliku nadal jest za długa, nazwę wyświetlaną ustawiono pusty ciąg, chyba że `bAtLeastName` jest różna od zera.  
  
##  <a name="getsize"></a>CRecentFileList::GetSize  
 Pobiera liczbę plików na liście MRU.  
  
```  
int GetSize() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczba plików w bieżącym ostatnio używanych (MRU) listy plików.  
  
##  <a name="operator_at"></a>[CRecentFileList::operator]  
 Przeciążenia indeksu dolnego ( `[]`) — operator zwraca pojedynczą `CString` określonego przez ten liczony od zera indeks `nIndex`.  
  
```  
CString& operator[ ](int nindex);
```  
  
### <a name="parameters"></a>Parametry  
 `nIndex`  
 Liczony od zera indeks `CString` w zestawie `CString`s.  
  
##  <a name="readlist"></a>CRecentFileList::ReadList  
 Odczytuje listy ostatnio używanych (MRU) pliku z rejestru lub aplikacji. Pliku INI.  
  
```  
virtual void ReadList();
```  
  
##  <a name="remove"></a>CRecentFileList::Remove  
 Usuwa plik z listy ostatnio używanych plików.  
  
```  
virtual void Remove(int nIndex);
```  
  
### <a name="parameters"></a>Parametry  
 `nIndex`  
 Liczony od zera indeks pliku, który ma zostać usunięty z listy ostatnio używanych plików (MRU).  
  
##  <a name="updatemenu"></a>CRecentFileList::UpdateMenu  
 Aktualizuje wyświetlanie menu listy ostatnio używanych plików.  
  
```  
virtual void UpdateMenu(CCmdUI* pCmdUI);
```  
  
### <a name="parameters"></a>Parametry  
 `pCmdUI`  
 Wskaźnik do [CCmdUI](../../mfc/reference/ccmdui-class.md) obiekt do menu listy plików ostatnio używanych (MRU).  
  
##  <a name="writelist"></a>CRecentFileList::WriteList  
 Zapisuje listy ostatnio używanych (MRU) plików w rejestrze lub w aplikacji. Pliku INI.  
  
```  
virtual void WriteList();
```  
  
## <a name="see-also"></a>Zobacz też  
 [Wykres hierarchii](../../mfc/hierarchy-chart.md)



