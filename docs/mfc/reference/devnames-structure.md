---
title: Struktura DEVNAMES | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- DEVNAMES
dev_langs:
- C++
helpviewer_keywords:
- DEVNAMES [MFC]
ms.assetid: aac97f60-2169-471a-ba5d-c0baed9eed9a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0c13167c42c6acbfcc5f3af500205eed6ab884d9
ms.sourcegitcommit: 208d445fd7ea202de1d372d3f468e784e77bd666
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/29/2018
ms.locfileid: "37121578"
---
# <a name="devnames-structure"></a>Struktura DEVNAMES
`DEVNAMES` Struktura zawiera ciągi, które sterownik urządzenia, a port wyjściowy nazwy drukarki.  
  
## <a name="syntax"></a>Składnia  
  
```  
typedef struct tagDEVNAMES { /* dvnm */  
    WORD wDriverOffset;  
    WORD wDeviceOffset;  
    WORD wOutputOffset;  
    WORD wDefault; */* driver,
    device,
    and port-name strings follow wDefault */  
} DEVNAMES;  
```  
  
#### <a name="parameters"></a>Parametry  
 *wDriverOffset*  
 (We/Wy) Określa przesunięcie w znakach zerem ciąg znaków zawierający nazwę pliku (bez rozszerzenia) sterownika urządzenia. W danych wejściowych ten ciąg jest używany do określenia drukarki, aby wyświetlić początkowo w oknie dialogowym.  
  
 *wDeviceOffset*  
 (We/Wy) Określa przesunięcie w znaków do ciągu zakończonego wartością null (maksymalnie 32 bajtach, włącznie z wartości null) zawierający nazwę urządzenia. Ten ciąg musi być taki sam jak `dmDeviceName` członkiem [DEVMODE](http://msdn.microsoft.com/library/windows/desktop/dd183565) struktury.  
  
 *wOutputOffset*  
 (We/Wy) Określa przesunięcie w znakach zerem ciąg zawierający nazwę urządzenia systemu DOS na nośnik fizyczny danych wyjściowych (port wyjściowy).  
  
 *wDefault*  
 Określa, czy ciągi są zawarte w `DEVNAMES` struktury zidentyfikować drukarki domyślnej. Ten ciąg jest używany, aby sprawdzić, czy drukarki domyślnej nie uległy zmianie od czasu ostatniej operacji drukowania. W danych wejściowych, jeśli jest ustawiona flaga DN_DEFAULTPRN, innych wartości w `DEVNAMES` struktury są porównywane z bieżącej drukarki domyślnej. Jeśli dowolne ciągi nie są zgodne, zostanie wyświetlony komunikat ostrzegawczy informującego o dokumentu może być konieczne ponownie sformatowany. W danych wyjściowych `wDefault` element członkowski zostanie zmieniona tylko wtedy, gdy zostało wyświetlone okno dialogowe Ustawienia wydruku i użytkownik wybrał przycisk OK. Flaga DN_DEFAULTPRN jest ustawiona, jeśli wybrano drukarki domyślnej. Jeśli wybrano drukarkę, flaga nie jest ustawiona. Wszystkie bity w tym elemencie członkowskim są zarezerwowane do użytku wewnętrznego przez procedurę — okno dialogowe drukowania.  
  
## <a name="remarks"></a>Uwagi  
 `PrintDlg` Funkcja używa tych ciągów zainicjować członków w oknie dialogowym drukowania zdefiniowane przez system. Gdy użytkownik zamyka okno dialogowe, informacje o wybranej drukarki jest zwracany w tej struktury.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** commdlg.h  
  
## <a name="see-also"></a>Zobacz też  
 [Struktury, style, wywołania zwrotne i mapy komunikatów](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CPrintDialog::CreatePrinterDC](../../mfc/reference/cprintdialog-class.md#createprinterdc)


