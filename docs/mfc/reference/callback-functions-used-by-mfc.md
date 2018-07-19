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
ms.openlocfilehash: 96db2ea0c28e14f7a8e614d94e18cd3fad3cda53
ms.sourcegitcommit: 6408139d5f5ff8928f056bde93d20eecb3520361
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/02/2018
ms.locfileid: "37339013"
---
# <a name="callback-functions-used-by-mfc"></a>Funkcje wywołania zwrotnego używane przez MFC
Trzy funkcje wywołania zwrotnego pojawiają się w bibliotece klas Microsoft Foundation. Te funkcje wywołania zwrotnego są przekazywane do [CDC::EnumObjects](../../mfc/reference/cdc-class.md#enumobjects), [CDC::GrayString](../../mfc/reference/cdc-class.md#graystring), i [CDC::SetAbortProc](../../mfc/reference/cdc-class.md#setabortproc). Należy pamiętać, że wszystkie funkcje wywołania zwrotnego musi przechwytują wyjątki MFC przed zwróceniem do Windows, ponieważ nie może być zgłaszane wyjątki granice wywołania zwrotnego. Aby uzyskać więcej informacji na temat wyjątków, zobacz artykuł [wyjątki](../../mfc/exception-handling-in-mfc.md).  

|Nazwa||  
|----------|-----------------|  
|[Funkcja wywołania zwrotnego dla CDC::EnumObjects](#enum_objects)||  
|[Funkcja wywołania zwrotnego dla CDC::GrayString](#graystring)||
|[Funkcja wywołania zwrotnego dla CDC::SetAbortProc](#setabortproc)|| 

## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxwin.h 

## <a name="enum_objects"></a> Funkcja wywołania zwrotnego dla CDC::EnumObjects
*ObjectFunc* nazwa jest symbolem zastępczym dla nazwy funkcji aplikacji.  
  
### <a name="syntax"></a>Składnia  
  
```  
int CALLBACK EXPORT ObjectFunc(
    LPSTR lpszLogObject,  
    LPSTR* lpData);
```  
  
### <a name="parameters"></a>Parametry  
 *lpszLogObject*  
 Wskazuje [LOGPEN](../../mfc/reference/logpen-structure.md) lub [LOGBRUSH](../../mfc/reference/logbrush-structure.md) struktura danych, która zawiera informacje dotyczące logicznej atrybutów obiektu.  
  
 *lpData*  
 Punkty danych podany w aplikacji jest przekazywany do `EnumObjects` funkcji.  
  
### <a name="return-value"></a>Wartość zwracana  
 Funkcja wywołania zwrotnego zwraca **int**. Wartość tego zwracany jest zdefiniowane przez użytkownika. Jeśli funkcja wywołania zwrotnego zwraca wartość 0, `EnumObjects` zatrzymuje wcześnie wyliczenia.  
  
### <a name="remarks"></a>Uwagi  
 Rzeczywista nazwa musi być eksportowany.  
  
## <a name="graystring"></a>  Funkcja wywołania zwrotnego dla CDC::GrayString
*OutputFunc* jest symbolem zastępczym dla nazwy funkcji wywołania zwrotnego z dostarczonych aplikacji.  
  
### <a name="syntax"></a>Składnia  
  
```  
BOOL CALLBACK EXPORT OutputFunc(
    HDC hDC,  
    LPARAM lpData,  
    int nCount);
```  
  
### <a name="parameters"></a>Parametry  
 *elementu hDC*  
 Identyfikuje kontekst urządzenia pamięci z mapą bitową w co najmniej szerokość i wysokość, określony przez `nWidth` i `nHeight` do `GrayString`.  
  
 *lpData*  
 Wskazuje ciąg znaków do rysowania.  
  
 *nCount*  
 Określa liczbę znaków w danych wyjściowych.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość zwracaną przez funkcję wywołania zwrotnego musi mieć wartość PRAWDA, informując o powodzeniu; w przeciwnym razie ma wartość FAŁSZ.  
  
### <a name="remarks"></a>Uwagi  
 Funkcja wywołania zwrotnego (*OutputFunc*) musi narysuj obraz względem współrzędnych (0,0) zamiast (*x*, *y*).  

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
  
 *Kod*  
 Określa, czy wystąpił błąd. Jeśli żaden błąd nie wystąpił, to 0. To SP_OUTOFDISK przypadku Menedżera wydruku jest obecnie wolne miejsce na dysku i więcej miejsca na dysku staną się dostępne, jeśli aplikacja oczekuje. Jeśli *kodu* jest SP_OUTOFDISK, aplikacja nie musi przerwać zadanie drukowania. Jeśli nie, musi on uzyskanie Menedżera wydruku przez wywołanie metody `PeekMessage` lub `GetMessage` funkcji Windows.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość zwracaną funkcji obsługi przerwania jest różna od zera, jeśli zadanie drukowania jest, aby kontynuować i 0, jeśli zostanie anulowane.  
  
### <a name="remarks"></a>Uwagi  
 Rzeczywista nazwa musi być eksportowany zgodnie z opisem w sekcji uwag [CDC::SetAbortProc](../../mfc/reference/cdc-class.md#setabortproc).  
 
  
## <a name="see-also"></a>Zobacz też  
 [Struktury, style, wywołania zwrotne i mapy komunikatów](structures-styles-callbacks-and-message-maps.md) [CDC::EnumObjects](../../mfc/reference/cdc-class.md#enumobjects) [CDC::SetAbortProc](../../mfc/reference/cdc-class.md#setabortproc) [CDC::GrayString](../../mfc/reference/cdc-class.md#graystring)

