---
title: Klasa CSocketFile | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CSocketFile
- AFXSOCK/CSocketFile
- AFXSOCK/CSocketFile::CSocketFile
dev_langs: C++
helpviewer_keywords: CSocketFile [MFC], CSocketFile
ms.assetid: 7924c098-5f72-40d6-989d-42800a47958f
caps.latest.revision: "24"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 48ab1428d2c02e51b02977c8457d28e20597cbb7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="csocketfile-class"></a>Klasa CSocketFile
A `CFile` obiekt używany do wysyłania i odbierania danych przez sieć za pośrednictwem usługi Windows Sockets.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CSocketFile : public CFile  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CSocketFile::CSocketFile](#csocketfile)|Konstruuje `CSocketFile` obiektu.|  
  
## <a name="remarks"></a>Uwagi  
 Możesz dołączyć `CSocketFile` do obiektu `CSocket` obiektu w tym celu. Możesz również i zwykle należy dołączyć `CSocketFile` do obiektu `CArchive` obiekt, aby uprościć wysyłania i odbierania danych za pomocą serializacji MFC.  
  
 Do serializowania danych (Wyślij), możesz wstawić je do archiwum, które wywołuje `CSocketFile` funkcje Członkowskie zapisu danych do `CSocket` obiektu. Do deserializacji (odbierać) dane, wyodrębnij z archiwum. Powoduje to archiwum do wywołania `CSocketFile` funkcje Członkowskie można odczytać danych z `CSocket` obiektu.  
  
> [!TIP]
>  Oprócz funkcji `CSocketFile` zgodnie z opisem w tym miejscu, można go jako obiekt autonomicznego pliku tak samo jak w przypadku `CFile`, jej klasy podstawowej. Można również użyć `CSocketFile` z dowolnej funkcji serializacji archiwum na podstawie MFC. Ponieważ `CSocketFile` nie obsługuje wszystkich `CFile`przez funkcję, niektóre domyślne MFC serializować funkcje nie są zgodne z `CSocketFile`. Jest to szczególnie istotne w `CEditView` klasy. Nie należy próbować serializować `CEditView` danych za pośrednictwem `CArchive` obiekt dołączony do `CSocketFile` przy użyciu `CEditView::SerializeRaw`; użyj **CEditView::Serialize** zamiast tego. `SerializeRaw` Funkcja oczekuje obiektu pliku ma funkcje, takie jak `Seek`, że `CSocketFile` nie ma.  
  
 Jeśli używasz `CArchive` z `CSocketFile` i `CSocket`, może wystąpić sytuacja, gdy **CSocket::Receive** wprowadza pętlę (przez **PumpMessages(FD_READ)**) oczekiwania na Żądana liczba bajtów. Wynika to z faktu Windows sockets Zezwalaj tylko jedno wywołanie ustawiania dla jednego powiadomienia FD_READ, ale `CSocketFile` i `CSocket` Zezwalaj na wiele wywołań otrzymanych na FD_READ. Jeśli otrzymasz FD_READ, gdy nie ma żadnych danych do odczytu, aplikacja zawiesza się. Jeśli nigdy nie otrzymasz innej FD_READ, aplikacja przestaje komunikacji za pośrednictwem gniazda.  
  
 Można rozwiązać ten problem w następujący sposób. W `OnReceive` metody klasy gniazda, wywołanie **CAsyncSocket::IOCtl (FIONREAD,...)**  przed wywołaniem `Serialize` metody klasy wiadomości gdy oczekiwane dane mają być odczytane z gniazda jest większy niż jeden pakiet TCP (maksymalna jednostka transmisji nośnika sieci zazwyczaj co najmniej 1096 bajtów). Jeśli rozmiar danych dostępne jest mniejsza niż jest to potrzebne, poczekaj, aż wszystkie dane odebrania, a następnie uruchomienie operacji odczytu.  
  
 W poniższym przykładzie `m_dwExpected` jest przybliżoną liczbę bajtów, które użytkownik zamierza odbierania. Zakłada się, że należy zadeklarować go w innym miejscu w kodzie.  
  
 [!code-cpp[NVC_MFCSocketThread#4](../../mfc/reference/codesnippet/cpp/csocketfile-class_1.cpp)]  
  
 Aby uzyskać więcej informacji, zobacz [Windows Sockets w MFC](../../mfc/windows-sockets-in-mfc.md), [Windows Sockets: przy użyciu gniazda z archiwami](../../mfc/windows-sockets-using-sockets-with-archives.md), jak również [interfejsu API systemu Windows Sockets 2](http://msdn.microsoft.com/library/windows/desktop/ms740673).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [Cfile —](../../mfc/reference/cfile-class.md)  
  
 `CSocketFile`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxsock.h  
  
##  <a name="csocketfile"></a>CSocketFile::CSocketFile  
 Konstruuje `CSocketFile` obiektu.  
  
```  
explicit CSocketFile(
    CSocket* pSocket,  
    BOOL bArchiveCompatible = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 `pSocket`  
 Gniazda do dołączenia do `CSocketFile` obiektu.  
  
 `bArchiveCompatible`  
 Określa, czy obiekt pliku jest przeznaczona do użytku z `CArchive` obiektu. Przekaż **FALSE** tylko wtedy, gdy chcesz użyć `CSocketFile` obiektu w sposób autonomicznych, jak w przypadku autonomicznego `CFile` obiektu, z pewnymi ograniczeniami. Ta flaga zmienia sposób `CArchive` obiekt dołączony do `CSocketFile` obiektu zarządza swojego bufora do odczytu.  
  
### <a name="remarks"></a>Uwagi  
 Destruktor obiektu powoduje usunięcie samej z obiektu gniazda podczas wykracza poza zakres lub usunięcia obiektu.  
  
> [!NOTE]
>  A `CSocketFile` może również służyć jako plik (ograniczone) bez `CArchive` obiektu. Domyślnie `CSocketFile` konstruktora `bArchiveCompatible` parametr jest **TRUE**. Określa, że obiekt pliku jest przeznaczona do użytku z archiwum. Aby użyć obiektu pliku bez archiwizacji, należy przekazać **FALSE** w `bArchiveCompatible` parametru.  
  
 W trybie "compatible Archiwizuj" `CSocketFile` obiektu zapewnia lepszą wydajność i zmniejsza zagrożenie "zakleszczenie." Zakleszczenie występuje, gdy gniazd nadawczych i odbiorczych oczekują na siebie lub do wspólnych zasobów. Taka sytuacja może wystąpić, jeśli `CArchive` obiektu doświadczenie z `CSocketFile` sposób za pomocą `CFile` obiektu. Z `CFile`, archiwum można założyć, że jeśli odbierze mniej bajtów niż zażądała na końcu pliku został osiągnięty.  
  
 Z `CSocketFile`, jednak dane są na podstawie komunikatu; bufor może zawierać wiele komunikatów, więc odbieranie mniej niż żądana liczba bajtów nie oznacza koniec pliku. Aplikacji nie są blokowane w tym przypadku na przykład z `CFile`, i będzie możliwe kontynuowanie, odczytywanie wiadomości z buforu, dopóki bufor jest pusty. [CArchive::IsBufferEmpty](../../mfc/reference/carchive-class.md#isbufferempty) funkcja jest przydatna do monitorowania stanu buforu archiwum w takim przypadku.  
  
 Aby uzyskać więcej informacji dotyczących korzystania z `CSocketFile`, zobacz artykuły [Windows Sockets: przy użyciu gniazda z archiwami](../../mfc/windows-sockets-using-sockets-with-archives.md) i [Windows Sockets: przykład z gniazda przy użyciu archiwa](../../mfc/windows-sockets-example-of-sockets-using-archives.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Cfile — klasa](../../mfc/reference/cfile-class.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Casyncsocket — klasa](../../mfc/reference/casyncsocket-class.md)   
 [Klasa CSocket](../../mfc/reference/csocket-class.md)
