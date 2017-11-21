---
title: Klasa CSimpleException | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CSimpleException
- AFX/CSimpleException
- AFX/CSimpleException::CSimpleException
- AFX/CSimpleException::GetErrorMessage
dev_langs: C++
helpviewer_keywords:
- CSimpleException [MFC], CSimpleException
- CSimpleException [MFC], GetErrorMessage
ms.assetid: be0eb8ef-e5b9-47d6-b0fb-efaff2d1e666
caps.latest.revision: "19"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 70ed8ecc43f8467ca4e0bdc0856b32f3510d85a0
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="csimpleexception-class"></a>Klasa CSimpleException
Ta klasa jest klasą bazową dla zasobu o znaczeniu krytycznym wyjątków MFC.  
  
## <a name="syntax"></a>Składnia  
  
```  
class AFX_NOVTABLE CSimpleException : public CException  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CSimpleException::CSimpleException](#csimpleexception)|Konstruktor.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CSimpleException::GetErrorMessage](#geterrormessage)|Zapewnia tekst o błędzie, który wystąpił.|  
  
## <a name="remarks"></a>Uwagi  
 `CSimpleException`jest klasą bazową dla zasobu o znaczeniu krytycznym wyjątków MFC i obsługuje własności i inicjowania komunikat o błędzie. Następujące klasy użyj `CSimpleException` jako klasy podstawowej:  
  
|||  
|-|-|  
|[Klasa CMemoryException](../../mfc/reference/cmemoryexception-class.md)|Wyjątek braku pamięci|  
|[Klasa CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md)|Żądania dla nieobsługiwanej operacji|  
|[Klasa CResourceException](../../mfc/reference/cresourceexception-class.md)|Zasobów systemu Windows nie została odnaleziona lub nie możliwość utworzenia|  
|[Klasa CUserException](../../mfc/reference/cuserexception-class.md)|Nie można odnaleźć wyjątek, który określa zasoby|  
|[Klasa CInvalidArgException](../../mfc/reference/cinvalidargexception-class.md)|Wyjątek, który wskazuje nieprawidłowy argument|  
  
 Ponieważ `CSimpleException` jest abstrakcyjna klasa podstawowa nie można zadeklarować `CSimpleException` obiekt bezpośrednio. Zamiast tego należy zadeklarować pochodnej obiektów, takich jak w poprzedniej tabeli. Jeśli są deklarowanie klasy pochodnej, należy skorzystać z poprzednich klas jako model.  
  
 Aby uzyskać więcej informacji, zobacz [cexception — klasa](../../mfc/reference/cexception-class.md) tematu i [obsługi wyjątków (MFC)](../../mfc/exception-handling-in-mfc.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [Cexception —](../../mfc/reference/cexception-class.md)  
  
 `CSimpleException`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afx.h  
  
##  <a name="csimpleexception"></a>CSimpleException::CSimpleException  
 Konstruktor.  
  
```  
CSimpleException();  
explicit CSimpleException(BOOL bAutoDelete);
```  
  
### <a name="parameters"></a>Parametry  
 `bAutoDelete`  
 Określ **TRUE** Jeśli pamięć `CSimpleException` obiektu przydzielone na stercie. Spowoduje to `CSimpleException` obiektu do usunięcia po **usunąć** funkcja członkowska jest wywoływana, aby usunąć wyjątku. Określ **FALSE** Jeśli `CSimpleException` na stosie lub obiektu jest obiekt globalny. W takim przypadku `CSimpleException` obiektu nie zostanie usunięte, gdy **usunąć** została wywołana funkcja elementu członkowskiego.  
  
### <a name="remarks"></a>Uwagi  
 Zwykle nigdy nie należy bezpośrednio wywoływać tego konstruktora. Funkcja, która zgłasza wyjątek, należy utworzyć wystąpienie `CException`-klasy i Wywołaj jego konstruktora lub powinien użycie MFC zgłosić funkcje, takie jak [afxthrowfileexception —](exception-processing.md#afxthrowfileexception), aby zgłosić wstępnie zdefiniowanego typu.  
  
##  <a name="geterrormessage"></a>CSimpleException::GetErrorMessage  
 Wywołanie tej funkcji Członkowskich, aby umieścić tekst o błędzie, który wystąpił.  
  
```  
virtual BOOL GetErrorMessage(
    LPTSTR lpszError,
    UINT  nMaxError,
    PUNIT  pnHelpContext = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszError`  
 Wskaźnik do buforu, który zostanie wyświetlony komunikat o błędzie.  
  
 `nMaxError`  
 Maksymalna liczba znaków, może przechowywać buforu, łącznie z **NULL** terminator.  
  
 `pnHelpContext`  
 Adres **UINT** który zostanie wyświetlony identyfikator pomocy kontekstu. Jeśli **NULL**, zostanie zwrócony żaden identyfikator.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli funkcja zakończy się pomyślnie; w przeciwnym razie wartość 0, jeśli tekst komunikatu Błąd nie jest dostępna.  
  
### <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji, zobacz [CException::GetErrorMessage](../../mfc/reference/cfileexception-class.md#geterrormessage).  
  
## <a name="see-also"></a>Zobacz też  
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Cexception — klasa](../../mfc/reference/cexception-class.md)   
 [Obsługa wyjątków](../../mfc/exception-handling-in-mfc.md)



