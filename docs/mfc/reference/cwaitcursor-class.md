---
title: Klasa CWaitCursor | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CWaitCursor
- AFXWIN/CWaitCursor
- AFXWIN/CWaitCursor::CWaitCursor
- AFXWIN/CWaitCursor::Restore
dev_langs:
- C++
helpviewer_keywords:
- CWaitCursor [MFC], CWaitCursor
- CWaitCursor [MFC], Restore
ms.assetid: 5dfae2ff-d7b6-4383-b0ad-91e0868c67b3
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 1cf5c850158e445e7695b85e540b1e0c162e621c
ms.sourcegitcommit: 54035dce0992ba5dce0323d67f86301f994ff3db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/03/2018
---
# <a name="cwaitcursor-class"></a>Klasa CWaitCursor
Zapewnia sposób jednego wiersza Pokaż kursora oczekiwania, który zazwyczaj jest wyświetlany jako Klepsydra podczas podczas wykonywania długotrwałej operacji.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CWaitCursor  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CWaitCursor::CWaitCursor](#cwaitcursor)|Konstruuje `CWaitCursor` obiektu i wyświetla kursor oczekiwania.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CWaitCursor::Restore](#restore)|Przywraca kursora oczekiwania po jest został zmieniony.|  
  
## <a name="remarks"></a>Uwagi  
 `CWaitCursor`nie ma klasy podstawowej.  
  
 Dobre praktyki programowaniu dla systemu Windows wymagają Wyświetla kursora oczekiwania, gdy wykonujesz operację, która ma zauważalnego ilość czasu.  
  
 Aby wyświetlić kursora oczekiwania, tylko definiuje `CWaitCursor` zmiennej przed kod, który wykonuje długotrwałej operacji. Konstruktor obiektu automatycznie powoduje, że kursor oczekiwania do wyświetlenia.  
  
 Gdy obiekt wykracza poza zakres (na końcu bloku, w którym `CWaitCursor` jest zadeklarowany jako obiekt), jego destruktora ustawia kursor do poprzedniego kursora. Innymi słowy obiekt wykonuje niezbędne oczyszczania automatycznie.  
  
> [!NOTE]
>  Ze względu na sposób ich konstruktory i destruktory działania `CWaitCursor` obiektów zawsze są deklarowane jako zmienne lokalne — nigdy nie jest zadeklarowany jako jako zmienne globalne nie są one przydzielane z **nowe**.  
  
 Jeśli operacja, która może spowodować, że kursor zostanie zmieniony, takie jak wyświetlanie okna komunikatu lub okno dialogowe, wywołaj [przywrócić](#restore) funkcji członkowskiej, aby przywrócić kursora oczekiwania. Można wywołać **przywrócić** nawet gdy kursor oczekiwania jest aktualnie wyświetlany.  
  
 Innym sposobem wyświetlenia kursora oczekiwania jest użycie kombinacji [CCmdTarget::BeginWaitCursor](../../mfc/reference/ccmdtarget-class.md#beginwaitcursor), [CCmdTarget::EndWaitCursor](../../mfc/reference/ccmdtarget-class.md#endwaitcursor)i być może [CCmdTarget::RestoreWaitCursor](../../mfc/reference/ccmdtarget-class.md#restorewaitcursor). Jednak `CWaitCursor` jest łatwiejsza w użyciu, ponieważ nie trzeba ustawić kursor do poprzedniego kursora po zakończeniu długotrwałej operacji.  
  
> [!NOTE]
>  Ustawia MFC i przywraca za pomocą kursora [CWinApp::DoWaitCursor](../../mfc/reference/cwinapp-class.md#dowaitcursor) funkcję wirtualną. Można zastąpić tę funkcję, aby zapewnić zachowanie niestandardowych.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `CWaitCursor`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxwin.h  
  
## <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCWindowing#62](../../mfc/reference/codesnippet/cpp/cwaitcursor-class_1.cpp)]  
  
##  <a name="cwaitcursor"></a>CWaitCursor::CWaitCursor  
 Aby wyświetlić kursora oczekiwania, po prostu zadeklarować `CWaitCursor` obiektu przed kod, który wykonuje długotrwałej operacji.  
  
```  
CWaitCursor();
```  
  
### <a name="remarks"></a>Uwagi  
 Konstruktor automatycznie powoduje, że kursor oczekiwania do wyświetlenia.  
  
 Gdy obiekt wykracza poza zakres (na końcu bloku, w którym `CWaitCursor` jest zadeklarowany jako obiekt), jego destruktora ustawia kursor do poprzedniego kursora. Innymi słowy obiekt wykonuje niezbędne oczyszczania automatycznie.  
  
 Można korzystać z faktu, że destruktor jest wywoływana na końcu bloku (która może być przed zakończeniem funkcji) w celu uaktywnienia kursora oczekiwania w tylko część funkcji. Ta technika jest wyświetlany w drugim przykładzie poniżej.  
  
> [!NOTE]
>  Ze względu na sposób ich konstruktory i destruktory działania `CWaitCursor` obiektów zawsze są deklarowane jako zmienne lokalne — nigdy nie jest zadeklarowany jako jako zmienne globalne nie są one przydzielane z **nowe**.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCWindowing#63](../../mfc/reference/codesnippet/cpp/cwaitcursor-class_2.cpp)]  
  
##  <a name="restore"></a>CWaitCursor::Restore  
 Aby przywrócić kursora oczekiwania, wywołanie tej funkcji po wykonaniu operacji, takich jak wyświetlanie okna komunikatu lub okno dialogowe, które może zmienić kursora oczekiwania na inny kursor.  
  
```  
void Restore();
```  
  
### <a name="remarks"></a>Uwagi  
 Jest OK, aby wywołać **przywrócić** nawet gdy kursor oczekiwania jest aktualnie wyświetlany.  
  
 Jeśli trzeba przywrócić oczekiwania kursor znajduje się w funkcji innego niż ten, w którym `CWaitCursor` jest zadeklarowany jako obiekt, można wywołać [CCmdTarget::RestoreWaitCursor](../../mfc/reference/ccmdtarget-class.md#restorewaitcursor).  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCWindowing#64](../../mfc/reference/codesnippet/cpp/cwaitcursor-class_3.cpp)]  
  
## <a name="see-also"></a>Zobacz też  
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [CCmdTarget::BeginWaitCursor](../../mfc/reference/ccmdtarget-class.md#beginwaitcursor)   
 [CCmdTarget::EndWaitCursor](../../mfc/reference/ccmdtarget-class.md#endwaitcursor)   
 [CCmdTarget::RestoreWaitCursor](../../mfc/reference/ccmdtarget-class.md#restorewaitcursor)   
 [CWinApp::DoWaitCursor](../../mfc/reference/cwinapp-class.md#dowaitcursor)   
 [Jak I: zmienić wskaźnik myszy w aplikacji Microsoft Foundation — klasa](http://go.microsoft.com/fwlink/p/?linkid=128044)



