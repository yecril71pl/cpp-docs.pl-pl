---
title: Klasa CArchiveException | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CArchiveException
- AFX/CArchiveException
- AFX/CArchiveException::CArchiveException
- AFX/CArchiveException::m_cause
- AFX/CArchiveException::m_strFileName
dev_langs: C++
helpviewer_keywords:
- CArchiveException [MFC], CArchiveException
- CArchiveException [MFC], m_cause
- CArchiveException [MFC], m_strFileName
ms.assetid: da31a127-e86c-41d1-b0b6-bed0865b1b49
caps.latest.revision: "21"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 1c2ca798bf3cac50e00627fc3986072af7b2ff94
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="carchiveexception-class"></a>Klasa CArchiveException
Reprezentuje stan wyjątek serializacji  
  
## <a name="syntax"></a>Składnia  
  
```  
class CArchiveException : public CException  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CArchiveException::CArchiveException](#carchiveexception)|Konstruuje `CArchiveException` obiektu.|  
  
### <a name="public-data-members"></a>Publiczne elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CArchiveException::m_cause](#m_cause)|Wskazuje przyczynę wyjątku.|  
|[CArchiveException::m_strFileName](#m_strfilename)|Określa nazwę pliku dla tego warunku wyjątku.|  
  
## <a name="remarks"></a>Uwagi  
 `CArchiveException` Klasa zawiera element członkowski danych publicznych, który wskazuje przyczynę wyjątku.  
  
 `CArchiveException`obiekty są konstruowane i generowany wewnątrz [CArchive](../../mfc/reference/carchive-class.md) funkcji elementów członkowskich. Można uzyskać dostępu do tych obiektów w zakresie **CATCH** wyrażenia. Kod przyczyny jest niezależna od systemu operacyjnego. Aby uzyskać więcej informacji na temat wyjątek podczas przetwarzania, zobacz [obsługi wyjątków (MFC)](../../mfc/exception-handling-in-mfc.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [Cexception —](../../mfc/reference/cexception-class.md)  
  
 `CArchiveException`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afx.h  
  
##  <a name="carchiveexception"></a>CArchiveException::CArchiveException  
 Konstruuje `CArchiveException` obiektu przechowywanie wartości `cause` w obiekcie.  
  
```  
CArchiveException(
    int cause = CArchiveException::none,  
    LPCTSTR lpszArchiveName = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `cause`  
 Zmienna Typ wyliczany wskazujący przyczynę wyjątek. Lista wyliczenia, zobacz [m_cause](#m_cause) element członkowski danych.  
  
 `lpszArchiveName`  
 Wskazuje ciąg zawierający nazwę `CArchive` obiektu wyjątku.  
  
### <a name="remarks"></a>Uwagi  
 Można utworzyć `CArchiveException` obiektów na stercie i throw samodzielnie lub pozwolić funkcji globalnej [afxthrowarchiveexception —](../../mfc/reference/exception-processing.md#afxthrowarchiveexception) traktować go dla Ciebie.  
  
 Nie używaj tego konstruktora bezpośrednio; Zamiast tego wywołania funkcji globalnej `AfxThrowArchiveException`.  
  
##  <a name="m_cause"></a>CArchiveException::m_cause  
 Określa przyczyną wyjątku.  
  
```  
int m_cause;  
```  
  
### <a name="remarks"></a>Uwagi  
 Ten element członkowski danych jest publiczny zmiennej typu `int`. Wartości są definiowane przez `CArchiveException` typ wyliczeniowy. Moduły wyliczające i ich znaczenie są następujące:  
  
- **CArchiveException::none** nie wystąpił żaden błąd.  
  
- **CArchiveException::genericException** nieokreślony błąd.  
  
- **CArchiveException::readOnly** próbowano zapisać w archiwum otwartym do załadowania.  
  
- **CArchiveException::endOfFile** Reached koniec pliku podczas czytania obiektu.  
  
- **CArchiveException::writeOnly** nastąpiła próba odczytu z archiwum otwartym do przechowywania.  
  
- **CArchiveException::badIndex** niepoprawny format pliku.  
  
- **CArchiveException::badClass** próby odczytania obiektu do obiektu niewłaściwego typu.  
  
- **CArchiveException::badSchema** próby odczytania obiektu w innej wersji klasy.  
  
    > [!NOTE]
    >  Te `CArchiveException` moduły wyliczające Przyczyna różnią się od `CFileException` spowodować wyliczenia.  
  
    > [!NOTE]
    > **CArchiveException::generic** jest przestarzały. Użyj **genericException** zamiast tego. Jeśli **ogólnego** jest używane w aplikacji i zbudowany z/CLR, wystąpią błędy składni, które nie są łatwe do odszyfrowania.  
  
##  <a name="m_strfilename"></a>CArchiveException::m_strFileName  
 Określa nazwę pliku dla tego warunku wyjątku.  
  
```  
CString m_strFileName;  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Cexception — klasa](../../mfc/reference/cexception-class.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [CArchive — klasa](../../mfc/reference/carchive-class.md)   
 [Afxthrowarchiveexception —](../../mfc/reference/exception-processing.md#afxthrowarchiveexception)   
 [Przetwarzanie wyjątków](../../mfc/reference/exception-processing.md)

