---
title: Klasa CSocketFile
ms.date: 11/04/2016
f1_keywords:
- CSocketFile
- AFXSOCK/CSocketFile
- AFXSOCK/CSocketFile::CSocketFile
helpviewer_keywords:
- CSocketFile [MFC], CSocketFile
ms.assetid: 7924c098-5f72-40d6-989d-42800a47958f
ms.openlocfilehash: f3fa73320ae34283b0cdac559111a53a879c031c
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57274275"
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

Możesz dołączyć `CSocketFile` obiekt `CSocket` obiekt w tym celu. Możesz również i zwykle Dołącz `CSocketFile` obiekt `CArchive` obiektu, aby uprościć wysyłania i odbierania danych za pomocą serializacji MFC.

Do serializowania danych (Wyślij), możesz wstawić go do archiwum, która wywołuje `CSocketFile` można zapisać danych do elementów członkowskich `CSocket` obiektu. Do deserializacji (odbieranie) dane, wyodrębnij z archiwum. Powoduje to archiwum do wywołania `CSocketFile` funkcji elementów członkowskich, które można odczytać danych z `CSocket` obiektu.

> [!TIP]
>  Poza używaniem `CSocketFile` zgodnie z opisem w tym miejscu, służy jako autonomiczny plik obiektu, podobnie jak w przypadku `CFile`, jej klasy bazowej. Można również użyć `CSocketFile` z dowolnej funkcji archiwum na podstawie serializacji MFC. Ponieważ `CSocketFile` nie obsługuje wszystkich `CFile`przez funkcje, w niektórych domyślnych MFC serializacji funkcje nie są zgodne z `CSocketFile`. Jest to szczególnie istotne w `CEditView` klasy. Nie należy próbować serializacji `CEditView` danych za pośrednictwem `CArchive` obiekt dołączony do `CSocketFile` przy użyciu `CEditView::SerializeRaw`; użyj `CEditView::Serialize` zamiast tego. `SerializeRaw` Funkcja oczekuje obiektu pliku, aby funkcje, takie jak `Seek`, które `CSocketFile` nie ma.

Kiedy używać `CArchive` z `CSocketFile` i `CSocket`, może wystąpić sytuacja, gdzie `CSocket::Receive` wprowadza pętlę (przez `PumpMessages(FD_READ)`) oczekiwania na żądanej ilości bajtów. Jest to spowodowane Windows sockets Zezwalaj tylko jedno wywołanie otrzymanych na powiadomienie FD_READ, ale `CSocketFile` i `CSocket` Zezwalaj na wiele wywołań otrzymanych na FD_READ. Jeśli nie ma żadnych danych do odczytu powoduje FD_READ, aplikacja zawiesza się. Jeśli nigdy nie uzyskasz innej FD_READ, aplikacja przestaje komunikacji za pośrednictwem gniazda.

Ten problem można rozwiązać w następujący sposób. W `OnReceive` metody klasy gniazda, wywołanie `CAsyncSocket::IOCtl(FIONREAD, ...)` przed wywołaniem `Serialize` metody klasy komunikat podczas oczekiwanych danych do odczytu z gniazda jest większy niż jeden pakiet TCP (maksymalna jednostka transmisji z nośnika sieci zazwyczaj co najmniej 1096 bajtów). Jeśli rozmiar danych dostępne jest mniejsza niż jest to potrzebne, poczekaj, aż wszystkie dane w celu odebrania, a dopiero potem zaczynają operacji odczytu.

W poniższym przykładzie `m_dwExpected` jest przybliżona liczba bajtów, które użytkownik oczekuje odbierania. Zakłada się, że trzeba je zadeklarować innym miejscu w kodzie.

[!code-cpp[NVC_MFCSocketThread#4](../../mfc/reference/codesnippet/cpp/csocketfile-class_1.cpp)]

Aby uzyskać więcej informacji, zobacz [Windows Sockets w MFC](../../mfc/windows-sockets-in-mfc.md), [Windows Sockets: Używanie gniazd z archiwami](../../mfc/windows-sockets-using-sockets-with-archives.md), a także [Windows Sockets 2 API](/windows/desktop/WinSock/windows-sockets-start-page-2).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CFile](../../mfc/reference/cfile-class.md)

`CSocketFile`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxsock.h

##  <a name="csocketfile"></a>  CSocketFile::CSocketFile

Konstruuje `CSocketFile` obiektu.

```
explicit CSocketFile(
    CSocket* pSocket,
    BOOL bArchiveCompatible = TRUE);
```

### <a name="parameters"></a>Parametry

*pSocket*<br/>
Gniazda, aby dołączyć do `CSocketFile` obiektu.

*bArchiveCompatible*<br/>
Określa, czy obiekt pliku jest do użytku z programem `CArchive` obiektu. Przekaż wartość FAŁSZ tylko wtedy, gdy chcesz używać `CSocketFile` obiektu w sposób autonomiczny, jak w przypadku autonomicznego `CFile` obiektu, z pewnymi ograniczeniami. Ta flaga zmienia sposób, w jaki `CArchive` obiekt dołączony do `CSocketFile` obiektu zarządza jej bufora do odczytu.

### <a name="remarks"></a>Uwagi

Destruktor obiektu powoduje usunięcie samej z obiektu gniazda gdy obiekt wykracza poza zakres lub został usunięty.

> [!NOTE]
>  A `CSocketFile` może również służyć jako plik (ograniczone) bez `CArchive` obiektu. Domyślnie `CSocketFile` firmy Konstruktor *bArchiveCompatible* parametr ma wartość TRUE. Określa, że plik jest do użytku z archiwum. Aby użyć obiektu pliku bez archiwum, Przekaż wartość FALSE w *bArchiveCompatible* parametru.

W trybie "archiwum compatible" `CSocketFile` obiekt zapewnia lepszą wydajność i zmniejsza zagrożenie "zakleszczenie." Zakleszczenie występuje, gdy gniazd nadawczych i oczekują od siebie lub dla wspólnego zasobu. Taka sytuacja może wystąpić, jeśli `CArchive` obiektu doświadczenie z `CSocketFile` sposób, jak za pomocą `CFile` obiektu. Za pomocą `CFile`, archiwum, można założyć, że jeśli odbierze mniej bajtów niż żądana go, na końcu pliku został osiągnięty.

Za pomocą `CSocketFile`, jednak dane są na podstawie komunikatu; bufor może zawierać wiele komunikatów, więc odbieranie mniej niż żądana liczba bajtów nie oznacza koniec pliku. Aplikacja nie są blokowane w tym przypadku na przykład za pomocą `CFile`, i można kontynuować, odczytywanie wiadomości z buforu, dopóki rozmiar buforu jest pusty. [CArchive::IsBufferEmpty](../../mfc/reference/carchive-class.md#isbufferempty) funkcja jest przydatna do monitorowania stanu bufora archiwum w takiej sytuacji.

Aby uzyskać więcej informacji na temat użytkowania `CSocketFile`, zobacz artykuły [Windows Sockets: Używanie gniazd z archiwami](../../mfc/windows-sockets-using-sockets-with-archives.md) i [Windows Sockets: Przykład gniazd korzystających z archiwów](../../mfc/windows-sockets-example-of-sockets-using-archives.md).

## <a name="see-also"></a>Zobacz także

[Klasa CFile](../../mfc/reference/cfile-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CAsyncSocket](../../mfc/reference/casyncsocket-class.md)<br/>
[Klasa CSocket](../../mfc/reference/csocket-class.md)
