---
title: Drukowanie programowe
ms.date: 11/04/2016
helpviewer_keywords:
- printing [MFC], active documents
- active documents [MFC], printing
- printing [MFC], programmatic
- IPrint interface
- printing [MFC]
ms.assetid: 3db0945b-5e13-4be4-86a0-6aecdae565bd
ms.openlocfilehash: eb8804610832f91f4b24487fddfe9c24a3799117
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/24/2019
ms.locfileid: "64342094"
---
# <a name="programmatic-printing"></a>Drukowanie programowe

OLE podane oznacza, że do unikatowego identyfikowania trwałego dokumentów (`GetClassFile`) i załadować je do ich skojarzonego kodu (`CoCreateInstance`, `QueryInterface(IID_IPersistFile)`, `QueryInterface(IID_IPersistStorage)`, `IPersistFile::Load`, i `IPersistStorage::Load`). Aby umożliwić dalsze drukowania dokumentów, zawieranie dokumentów aktywnych (przy użyciu istniejącego projektu OLE nie są dostarczane z OLE 2.0 pierwotnie) wprowadza base standardowy interfejs drukowania, `IPrint`, jest ogólnie dostępna w ramach dowolnego obiektu, który można załadować Stan trwały używanego typu dokumentu. Każdy widok aktywnego dokumentu może opcjonalnie obsługiwać `IPrint` interfejs do tych możliwości.

`IPrint` Interfejsu jest zdefiniowana w następujący sposób:

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

Klienci i kontenery po prostu użyć `IPrint::Print` nakazać dokument, aby wydrukował sam siebie po załadowaniu tego dokumentu, określając drukowania flagi kontrolne, urządzenie docelowe, strony, aby wydrukować oraz dodatkowe opcje. Klienta można także kontrolować kontynuacja drukowanie za pomocą interfejsu `IContinueCallback` (patrz poniżej).

Ponadto `IPrint::SetInitialPageNum` obsługuje możliwość drukują szeregi dokumentów zgodnie z jedną przy numerowanie strony bezproblemowo oczywiście korzyść dla kontenerów dokumentów aktywnych, takich jak Office Binder. `IPrint::GetPageInfo` sprawia, że wyświetlane informacje o podziale proste, umożliwiając obiekt wywołujący, aby pobrać początkowy stronie numer wcześniej przeszły testy `SetInitialPageNum` (lub dokumentu wewnętrzny domyślny numer strony początkowej) i liczbę stron w dokumencie.

Obiekty, które obsługują `IPrint` są oznaczone w rejestrze z kluczem "Printable" przechowywane na podstawie identyfikatora CLSID obiektu:

HKEY_CLASSES_ROOT\CLSID\\{...} \Printable

`IPrint` Zazwyczaj jest wdrażana w ten sam obiekt, który obsługuje `IPersistFile` lub `IPersistStorage`. Obiekty wywołujące należy pamiętać, możliwość programowe drukowanie trwały stan niektóre klasy przez wyszukiwanie w rejestrze dla klucza "Printable". Obecnie "Drukowalnych" wskazuje obsługę co najmniej `IPrint`; inne interfejsy mogą być zdefiniowane w przyszłości, który będzie wówczas dostępne za pośrednictwem `QueryInterface` gdzie `IPrint` po prostu reprezentuje podstawowy poziom pomocy technicznej.

Podczas drukowania procedury można, klienta lub kontener, który zainicjował drukowania do kontrolowania, czy drukowanie powinno być kontynuowane. Na przykład kontener może obsługiwać należy zakończyć zadanie drukowania możliwie jak polecenie "Stop Print". Obsługa tej możliwości, klient drukowalnych obiektu można zaimplementować obiekt sink małych powiadomienia, za pomocą interfejsu `IContinueCallback`:

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

Ten interfejs jest bardzo przydatne jako funkcja wywołania zwrotnego kontynuacji ogólnego ma miejsce różnych procedur kontynuacji w interfejsie API systemu Win32 (takie jak `AbortProc` związane z drukowaniem i `EnumMetafileProc` metaplik wyliczenia). Ten sposób ten projekt interfejsu jest przydatny do szerokiej gamy czasochłonnych procesów.

W przypadku najbardziej ogólny `IContinueCallback::FContinue` funkcja jest wywoływana okresowo przez dowolnego długotrwałym procesem. Obiekt sink zwraca wartość S_OK, aby kontynuować operację i S_FALSE, aby zatrzymać tę procedurę, tak szybko, jak to możliwe.

`FContinue`, jednak nie jest używany w kontekście `IPrint::Print`; zamiast drukowanie używa `IContinueCallback::FContinuePrint`. Dowolny obiekt drukowania należy okresowo wywoływać `FContinuePrinting` przekazywanie liczbę stron, które zostały drukowanie, numer strony, drukowanie i dodatkowy ciąg opisujący stan drukowania, którego klient może być wyświetlany dla użytkownika (na przykład "Page 5 19").

## <a name="see-also"></a>Zobacz także

[Kontenery dokumentów aktywnych](../mfc/active-document-containers.md)
