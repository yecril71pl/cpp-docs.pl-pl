---
title: Drukowanie programowe | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- printing [MFC], active documents
- active documents [MFC], printing
- printing [MFC], programmatic
- IPrint interface
- printing [MFC]
ms.assetid: 3db0945b-5e13-4be4-86a0-6aecdae565bd
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 927a5d9b4bea41157c8cfac6f3dbfe42fc323bb2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="programmatic-printing"></a>Drukowanie programowe
OLE podane środki do unikatowego identyfikowania trwałe dokumentów (**GetClassFile**) i załadować je do ich skojarzonego kodu (`CoCreateInstance`, **QueryInterface(IID_IPersistFile)**, **QueryInterface(IID_IPersistStorage)**, **IPersistFile::Load**, i **IPersistStorage::Load**). Aby umożliwić drukowanie dokumentów, zawieranie dokumentów aktywnych (przy użyciu istniejącego projektu OLE nie zostały wydane z OLE 2.0 pierwotnie) wprowadzono base standard interfejsu drukowania, `IPrint`, ogólnie dostępna za pośrednictwem wszystkich obiektów, które można załadować Stan trwały typu dokumentu. Każdy widok aktywnego dokumentu może opcjonalnie obsługiwać **iprint —** interfejsu zapewniają następujące możliwości.  
  
 `IPrint` Interfejsu jest zdefiniowane w następujący sposób:  
  
```  
interface IPrint : IUnknown  
    {  
    HRESULT SetInitialPageNum([in] LONG nFirstPage);  
    HRESULT GetPageInfo(  
        [out] LONG *pnFirstPage,  
        [out] LONG *pcPages);  
    HRESULT Print(  
        [in] DWORD grfFlags,  
        [in,out] DVTARGETDEVICE **pptd,  
        [in,out] PAGESET ** ppPageSet,  
        [in,out] STGMEDIUM **ppstgmOptions,  
        [in] IContinueCallback* pCallback,  
        [in] LONG nFirstPage,  
        [out] LONG *pcPagesPrinted,  
        [out] LONG *pnPageLast);  
    };  
```  
  
 Klienci i kontenery po prostu użyć **IPrint::Print** nakazać dokument Drukuj, sama po załadowaniu tego dokumentu, określając drukowania flagi kontrolne, urządzenie docelowe, strony do drukowania oraz dodatkowe opcje. Klienta można także sterować kontynuacja drukowanie za pośrednictwem interfejsu `IContinueCallback` (patrz poniżej).  
  
 Ponadto **IPrint::SetInitialPageNum** obsługuje możliwość drukowania serii dokumentów, zgodnie z jedną poprzez numerowania strony bezproblemowo, oczywiście korzyści dla kontenerów dokumentów aktywnych, takich jak Office Binder. **IPrint::GetPageInfo** umożliwia wyświetlanie informacji podział na strony prostego przez obiekt wywołujący, aby pobrać początkowej strony numer wcześniej przekazany do **SetInitialPageNum** (lub dokumentu wewnętrznego ustawienia domyślnego numer strony początkowej) i liczba stron w dokumencie.  
  
 Obiekty obsługujące `IPrint` są oznaczone w rejestrze z kluczem "Printable" przechowywane na podstawie identyfikatora CLSID obiektu:  
  
 HKEY_CLASSES_ROOT\CLSID\\{...} \Printable  
  
 `IPrint`Zazwyczaj jest zaimplementowany dla tego samego obiektu, który obsługuje albo `IPersistFile` lub `IPersistStorage`. Obiekty wywołujące należy zwrócić uwagę możliwość programowane drukowanie trwały stan niektóre klasy przez wyszukiwanie w rejestrze dla klucza "Printable". Obecnie "Drukowalnych" wskazuje obsługę co najmniej `IPrint`; inne interfejsy może być zdefiniowana w przyszłości, który będzie wówczas dostępna za pośrednictwem `QueryInterface` gdzie **iprint —** po prostu reprezentuje podstawowym poziomie pomocy technicznej.  
  
 Podczas drukowania procedury można, klienta lub kontenera, który zainicjował drukowanie do kontrolowania, czy powinno być kontynuowane drukowania. Na przykład kontener może obsługiwać "Zatrzymaj drukowanie" polecenie, które należy jak najszybciej zakończyć zadania drukowania. Obsługa tej możliwości, klient drukowalnych obiektu można zaimplementować obiekt sink małych powiadomień przy użyciu interfejsu `IContinueCallback`:  
  
```  
interface IContinueCallback : IUnknown  
    {  
    HRESULT FContinue(void);  
    HRESULT FContinuePrinting(  
        [in] LONG cPagesPrinted,  
        [in] LONG nCurrentPage,  
        [in] LPOLESTR pszPrintStatus);  
    };  
```  
  
 Ten interfejs ma służyć jako funkcję wywołania zwrotnego kontynuacji ogólnego, który odbywa się z różnych procedur kontynuacji w interfejsie API Win32 (takich jak **AbortProc** do drukowania i  **EnumMetafileProc** wyliczenia metaplik). W związku z tym ten projekt interfejsu jest przydatne w wielu różnych procesów czasochłonna.  
  
 W przypadku najbardziej ogólnym **IContinueCallback::FContinue** funkcja jest wywoływana przez żaden proces, długotrwałą, okresowo. Zwraca obiekt sink `S_OK` aby kontynuować operację, i **S_FALSE** aby jak najszybciej zatrzymać tę procedurę.  
  
 **FContinue**, jednak nie jest używana w kontekście **IPrint::Print**; zamiast drukowanie używa **IContinueCallback::FContinuePrint**. Dowolny obiekt drukowania okresowo powinny wywoływać **FContinuePrinting** przekazywanie liczbę stron, które zostały drukowania, numer strony drukowanej i dodatkowy ciąg opisujący stan drukowania, którego klient może być wyświetlana użytkownikowi (na przykład "5 strony 19").  
  
## <a name="see-also"></a>Zobacz też  
 [Kontenery dokumentów aktywnych](../mfc/active-document-containers.md)

