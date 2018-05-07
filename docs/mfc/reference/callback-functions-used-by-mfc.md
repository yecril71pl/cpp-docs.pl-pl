---
title: Funkcje wywołania zwrotnego używane przez MFC | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.mfc.functions
dev_langs:
- C++
helpviewer_keywords:
- callback functions [MFC], MFC
- MFC, callback functions
- functions [MFC], callback
- callback functions [MFC]
ms.assetid: b2a6857c-fdd3-45ec-8fd8-2e71fac77582
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ce96d90506176812ffb70b580c9d95a38c65fa19
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="callback-functions-used-by-mfc"></a>Funkcje wywołania zwrotnego używane przez MFC
Trzy funkcje wywołania zwrotnego są wyświetlane w programie Microsoft Foundation Class Library. Te funkcje wywołania zwrotnego są przekazywane do [CDC::EnumObjects](../../mfc/reference/cdc-class.md#enumobjects), [CDC::GrayString](../../mfc/reference/cdc-class.md#graystring), i [CDC::SetAbortProc](../../mfc/reference/cdc-class.md#setabortproc). Należy pamiętać, że wszystkie funkcje wywołania zwrotnego musi przechwytują wyjątki MFC przed zwróceniem do systemu Windows, ponieważ nie może być wyjątek w granicach wywołania zwrotnego. Aby uzyskać więcej informacji o wyjątkach, zobacz artykuł [wyjątki](../../mfc/exception-handling-in-mfc.md).  

|Nazwa||  
|----------|-----------------|  
|[Funkcja wywołania zwrotnego dla CDC::EnumObjects](#enum_objects)||  
|[Funkcja wywołania zwrotnego dla CDC::GrayString](#graystring)||
|[Funkcja wywołania zwrotnego dla CDC::SetAbortProc](#setabortproc)|| 

## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxwin.h 

## <a name="enum_objects"></a> Funkcja wywołania zwrotnego dla CDC::EnumObjects
*ObjectFunc* nazwy jest symbolem zastępczym dla nazwy funkcji aplikacji.  
  
### <a name="syntax"></a>Składnia  
  
```  
int CALLBACK EXPORT ObjectFunc(
    LPSTR lpszLogObject,  
    LPSTR* lpData);
```  
  
### <a name="parameters"></a>Parametry  
 *lpszLogObject*  
 Wskazuje [LOGPEN](../../mfc/reference/logpen-structure.md) lub [LOGBRUSH](../../mfc/reference/logbrush-structure.md) struktura danych, która zawiera informacje dotyczące logicznej atrybutów obiektu.  
  
 `lpData`  
 Punkty danych dostarczonych aplikacji przekazany do `EnumObjects` funkcji.  
  
### <a name="return-value"></a>Wartość zwracana  
 Funkcja wywołania zwrotnego `int`. Wartość tego zwracany jest zdefiniowane przez użytkownika. Jeśli funkcja wywołania zwrotnego zwraca wartość 0, `EnumObjects` zatrzymuje wczesne wyliczenia.  
  
### <a name="remarks"></a>Uwagi  
 Musi być eksportowany rzeczywistą nazwą.  
  
## <a name="graystring"></a>  Funkcja wywołania zwrotnego dla CDC::GrayString
*OutputFunc* to symbol zastępczy nazwą funkcji dostarczone przez aplikację wywołania zwrotnego.  
  
### <a name="syntax"></a>Składnia  
  
```  
BOOL CALLBACK EXPORT OutputFunc(
    HDC hDC,  
    LPARAM lpData,  
    int nCount);
```  
  
### <a name="parameters"></a>Parametry  
 `hDC`  
 Identyfikuje kontekst urządzenia pamięci z mapą bitową co najmniej szerokości i wysokości określony przez `nWidth` i `nHeight` do `GrayString`.  
  
 `lpData`  
 Wskazuje ciąg znaków do rysowania.  
  
 `nCount`  
 Określa liczbę znaków do danych wyjściowych.  
  
### <a name="return-value"></a>Wartość zwracana  
 Funkcja wywołania zwrotnego zwracana wartość musi być **TRUE** informując o powodzeniu; w przeciwnym razie jest **FALSE**.  
  
### <a name="remarks"></a>Uwagi  
 Funkcja wywołania zwrotnego (*OutputFunc*) należy narysować obrazu względem współrzędnych (0,0) zamiast (*x*, *y*).  

## <a name="setabortproc"></a>  Funkcja wywołania zwrotnego dla CDC::SetAbortProc
Nazwa *AbortFunc* jest symbolem zastępczym dla nazwy funkcji aplikacji.  
  
### <a name="syntax"></a>Składnia  
  
```  
BOOL CALLBACK EXPORT AbortFunc(
    HDC hPr,  
    int code);
```  
  
### <a name="parameters"></a>Parametry  
 *hPr*  
 Identyfikuje kontekst urządzenia.  
  
 `code`  
 Określa, czy wystąpił błąd. Jeśli wystąpił błąd nie jest 0. Jest **SP_OUTOFDISK** Jeśli Menedżera wydruku jest obecnie mało miejsca na dysku i stanie się dostępna, gdy aplikacja oczekuje więcej miejsca na dysku. Jeśli `code` jest **SP_OUTOFDISK**przerwać zadanie drukowania nie ma aplikacji. Jeśli nie, musi on uzyskanie Menedżera wydruku przez wywołanie metody **PeekMessage** lub **GetMessage** funkcji systemu Windows.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość zwracana funkcji obsługi przerwania jest różna od zera, jeśli zadanie drukowania jest kontynuowanie i 0, jeśli jest ona anulowana.  
  
### <a name="remarks"></a>Uwagi  
 Rzeczywista nazwa musi być eksportowany zgodnie z opisem w sekcji uwag [CDC::SetAbortProc](../../mfc/reference/cdc-class.md#setabortproc).  
 
  
## <a name="see-also"></a>Zobacz też  
 [Struktury, style, wywołania zwrotne i mapy komunikatów](structures-styles-callbacks-and-message-maps.md) [CDC::EnumObjects](../../mfc/reference/cdc-class.md#enumobjects) [CDC::SetAbortProc](../../mfc/reference/cdc-class.md#setabortproc) [CDC::GrayString](../../mfc/reference/cdc-class.md#graystring)

