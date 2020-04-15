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
ms.openlocfilehash: 83810a05925e5c8302240b61d95c131fdd78b426
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81318161"
---
# <a name="csocketfile-class"></a>Klasa CSocketFile

Obiekt `CFile` używany do wysyłania i odbierania danych przez sieć za pośrednictwem gniazd systemu Windows.

## <a name="syntax"></a>Składnia

```
class CSocketFile : public CFile
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CSocketFile::CSocketFile](#csocketfile)|Konstruuje `CSocketFile` obiekt.|

## <a name="remarks"></a>Uwagi

W tym `CSocketFile` celu obiekt `CSocket` można dołączyć do obiektu. Można również i zwykle dołączyć `CSocketFile` obiekt do `CArchive` obiektu, aby uprościć wysyłanie i odbieranie danych przy użyciu serializacji MFC.

Aby serializować (wysyłać) dane, należy wstawić je do archiwum, które wywołuje `CSocketFile` funkcje członkowskie do zapisu danych do `CSocket` obiektu. Aby deserialize (odbierać) dane, należy wyodrębnić z archiwum. Powoduje to, że `CSocketFile` archiwum do wywoływania funkcji członkowskich do odczytu `CSocket` danych z obiektu.

> [!TIP]
> Oprócz `CSocketFile` używania zgodnie z opisem tutaj, można go używać jako autonomicznego obiektu pliku, tak jak można z `CFile`, jego klasy podstawowej. Można również `CSocketFile` użyć z dowolnymi funkcjami serializacji MFC opartych na archiwum. Ponieważ `CSocketFile` nie obsługuje `CFile`wszystkich funkcji, niektóre domyślne funkcje serializacji `CSocketFile`MFC nie są zgodne z programem . Dotyczy to w szczególności `CEditView` klasy. Nie należy próbować `CEditView` serializować `CArchive` danych za pośrednictwem `CSocketFile` obiektu `CEditView::SerializeRaw`dołączonego do obiektu przy użyciu ; zamiast `CEditView::Serialize` tego użyć. Funkcja `SerializeRaw` oczekuje, że obiekt pliku ma `Seek`funkcje, takie jak , które `CSocketFile` nie mają.

Podczas korzystania `CArchive` `CSocketFile` z `CSocket`i , może `CSocket::Receive` wystąpić sytuacja, w `PumpMessages(FD_READ)`której wchodzi w pętli (by) oczekiwanie na żądaną ilość bajtów. Dzieje się tak, ponieważ gniazda systemu Windows zezwalają tylko `CSocketFile` `CSocket` na jedno wywołanie recv na powiadomienie FD_READ, ale zezwalają na wiele wywołań recv na FD_READ. Jeśli otrzymasz FD_READ, gdy nie ma żadnych danych do odczytu, aplikacja zawiesza się. Jeśli nigdy nie otrzymasz innego FD_READ, aplikacja przestaje komunikować się za pośrednictwem gniazda.

Można rozwiązać ten problem w następujący sposób. W `OnReceive` metodzie klasy gniazda `CAsyncSocket::IOCtl(FIONREAD, ...)` wywołać przed `Serialize` wywołaniem metody klasy wiadomości, gdy oczekiwane dane do odczytu z gniazda przekracza rozmiar jednego pakietu TCP (maksymalna jednostka transmisji medium sieciowego, zwykle co najmniej 1096 bajtów). Jeśli rozmiar dostępnych danych jest mniejszy niż jest to potrzebne, poczekaj na odebranie wszystkich danych, a dopiero potem rozpocznij operację odczytu.

W poniższym `m_dwExpected` przykładzie jest przybliżona liczba bajtów, które użytkownik oczekuje, aby otrzymać. Zakłada się, że deklarujesz go w innym miejscu w kodzie.

[!code-cpp[NVC_MFCSocketThread#4](../../mfc/reference/codesnippet/cpp/csocketfile-class_1.cpp)]

Aby uzyskać więcej informacji, zobacz [Gniazda systemu Windows w MFC](../../mfc/windows-sockets-in-mfc.md), Windows [Sockets: Using Sockets with Archives](../../mfc/windows-sockets-using-sockets-with-archives.md), a także [Windows Sockets 2 API](/windows/win32/WinSock/windows-sockets-start-page-2).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[Cfile](../../mfc/reference/cfile-class.md)

`CSocketFile`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxsock.h

## <a name="csocketfilecsocketfile"></a><a name="csocketfile"></a>CSocketFile::CSocketFile

Konstruuje `CSocketFile` obiekt.

```
explicit CSocketFile(
    CSocket* pSocket,
    BOOL bArchiveCompatible = TRUE);
```

### <a name="parameters"></a>Parametry

*pSocket*<br/>
Gniazdo do mocowania `CSocketFile` do obiektu.

*bArchiwowanie kompatybilne*<br/>
Określa, czy obiekt pliku jest `CArchive` używany z obiektem. Przekaż FALSE tylko wtedy, `CSocketFile` gdy chcesz użyć obiektu w sposób autonomiczny, tak jak `CFile` obiekt autonomiczny, z pewnymi ograniczeniami. Ta flaga `CArchive` zmienia sposób, `CSocketFile` w jaki obiekt dołączony do obiektu zarządza buforem do odczytu.

### <a name="remarks"></a>Uwagi

Destruktor obiektu odłącza się od obiektu gniazda, gdy obiekt wykracza poza zakres lub jest usuwany.

> [!NOTE]
> A `CSocketFile` może być również używany jako (ograniczony) plik bez `CArchive` obiektu. Domyślnie `CSocketFile` konstruktora *bArchiveCompatible* parametr jest PRAWDA. Określa to, że obiekt pliku jest przeznaczony do użytku z archiwum. Aby użyć obiektu pliku bez archiwum, przekaż FAŁSZ w parametrze *bArchiveCompatible.*

W trybie "archiwum `CSocketFile` kompatybilnym" obiekt zapewnia lepszą wydajność i zmniejsza niebezpieczeństwo "zakleszczenia". Zakleszczenie występuje, gdy zarówno wysyłanie i odbieranie gniazd czekają na siebie nawzajem lub dla wspólnego zasobu. Taka sytuacja może `CArchive` wystąpić, jeśli `CSocketFile` obiekt pracował z `CFile` tym, jak robi z obiektem. W `CFile`przypadku archiwum można założyć, że jeśli otrzyma mniej bajtów niż żądano, osiągnięto koniec pliku.

Z `CSocketFile`, jednak dane są oparte na wiadomości; bufor może zawierać wiele komunikatów, więc odbieranie mniej niż liczba żądanych bajtów nie oznacza końca pliku. Aplikacja nie blokuje w tym przypadku, `CFile`jak może z , i może kontynuować odczytywanie komunikatów z buforu, aż bufor jest pusty. [CArchive::IsBufferEmpty](../../mfc/reference/carchive-class.md#isbufferempty) funkcja jest przydatna do monitorowania stanu buforu archiwum w takim przypadku.

Aby uzyskać więcej informacji `CSocketFile`na temat korzystania z , zobacz artykuły [Windows Sockets: Using Sockets with Archives](../../mfc/windows-sockets-using-sockets-with-archives.md) and [Windows Sockets: Example of Sockets Using Archives](../../mfc/windows-sockets-example-of-sockets-using-archives.md).

## <a name="see-also"></a>Zobacz też

[Klasa CFile](../../mfc/reference/cfile-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CAsyncSocket](../../mfc/reference/casyncsocket-class.md)<br/>
[Klasa CSocket](../../mfc/reference/csocket-class.md)
