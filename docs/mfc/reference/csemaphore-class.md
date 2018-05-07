---
title: Klasa CSemaphore | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CSemaphore
- AFXMT/CSemaphore
- AFXMT/CSemaphore::CSemaphore
dev_langs:
- C++
helpviewer_keywords:
- CSemaphore [MFC], CSemaphore
ms.assetid: 385fc7e4-8f86-4be2-85e1-d23b38c12f7f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2f3c5f7cb354bb4889c528fc55459eabcb032709
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="csemaphore-class"></a>Klasa CSemaphore
Obiekt klasy `CSemaphore` reprezentuje "semafora" — obiekt synchronizacji, który zapewnia ograniczoną liczbę wątków w jeden lub więcej procesów dostępu Maintains do liczba to liczba wątków obecnie uzyskują dostęp do określonego zasobu.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CSemaphore : public CSyncObject  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CSemaphore::CSemaphore](#csemaphore)|Konstruuje `CSemaphore` obiektu.|  
  
## <a name="remarks"></a>Uwagi  
 Semaforów są przydatne w kontrolowania dostępu do zasobu udostępnionego, który może obsługiwać tylko ograniczoną liczbę użytkowników. Bieżąca liczba `CSemaphore` obiekt jest liczby dodatkowych użytkowników. Jeśli licznik osiągnie wartość zero, wszystkie próbuje użyć zasobów kontrolowane przez **CSemaphore** obiekt zostanie wstawiony do kolejki systemu i poczekaj na ich albo limitu czasu lub liczba przekracza 0. Maksymalna liczba użytkowników, którzy mogą korzystać z kontrolą zasobu w tym samym czasie jest określana podczas budowy `CSemaphore` obiektu.  
  
 Aby użyć **CSemaphore** obiektów, utworzyć `CSemaphore` obiektu, gdy potrzebny jest. Określ nazwę semafora czekać, a aplikacji należy początkowo jest jej właścicielem. Następnie można uzyskać dostęp semafora po powrocie z konstruktora. Wywołanie [CSyncObject::Unlock](../../mfc/reference/csyncobject-class.md#unlock) po zakończeniu dostępu do kontrolowanego zasobu.  
  
 Alternatywna metoda przy użyciu `CSemaphore` obiektów jest dodanie do zmiennej typu `CSemaphore` jako element członkowski danych klasy do formantu. Podczas konstruowania obiektu kontrolowanego, należy wywołać konstruktora z `CSemaphore` określenie pierwszy element członkowski danych dostępu count, liczba maksymalna dostępu, nazwa semafora (jeśli będzie on używany przez granice procesu) i potrzeby atrybutów zabezpieczeń.  
  
 Dostęp do zasobów kontrolowane przez `CSemaphore` obiektów w ten sposób, najpierw Utwórz zmienną obu typów [CSingleLock](../../mfc/reference/csinglelock-class.md) lub typ [CMultiLock](../../mfc/reference/cmultilock-class.md) w funkcji członkowskiej dostępu do tego zasobu. Następnie wywołaj zablokować obiektu `Lock` funkcji członkowskiej (na przykład [CSingleLock::Lock](../../mfc/reference/csinglelock-class.md#lock)). W tym momencie z wątku zostanie albo uzyskać dostęp do zasobu, poczekaj zasobu zwolnione i uzyskać dostęp lub zaczekaj zasobów do zwolnienia i limit czasu, można uzyskać dostęp do zasobu. W każdym przypadku zasobu uzyskaniu w sposób wątkowo. Aby zwolnić zasobu, użyj obiektu blokady `Unlock` funkcji członkowskiej (na przykład [CSingleLock::Unlock](../../mfc/reference/csinglelock-class.md#unlock)), lub zezwala na wykraczać poza zakres obiektu blokady.  
  
 Alternatywnie można utworzyć **CSemaphore** obiekt autonomiczny i do niego dostęp jawnie przed podjęciem próby dostępu do kontrolowanego zasobu. Ta metoda podczas jaśniejszy osobie odczytywania kodu źródłowego, jest bardziej podatne na błędy.  
  
 Aby uzyskać więcej informacji na temat sposobu użycia **CSemaphore** obiektów, zobacz artykuł [Multithreading: jak używać klas synchronizacji](../../parallel/multithreading-how-to-use-the-synchronization-classes.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CSyncObject](../../mfc/reference/csyncobject-class.md)  
  
 `CSemaphore`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxmt.h  
  
##  <a name="csemaphore"></a>  CSemaphore::CSemaphore  
 Konstruuje nazwane i nienazwane `CSemaphore` obiektu.  
  
```  
CSemaphore(
    LONG lInitialCount = 1,  
    LONG lMaxCount = 1,  
    LPCTSTR pstrName = NULL,  
    LPSECURITY_ATTRIBUTES lpsaAttributes = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 *lInitialCount*  
 Liczba przypadków użycia początkowej semaforów. Musi być większa lub równa 0 i mniejsza niż lub równa `lMaxCount`.  
  
 `lMaxCount`  
 Maksymalne wykorzystanie Licznik semafora. Musi być większa niż 0.  
  
 `pstrName`  
 Nazwa semafora. Musi być dostarczona, jeśli semafora będą mieli dostęp przez granice procesu. Jeśli `NULL`, obiekt zostanie bez nazwy. Jeśli nazwa pasuje do istniejącego semafora, konstruktora tworzy nową `CSemaphore` obiektu, który odwołuje się do semafor o tej nazwie. Jeśli nazwa pasuje do istniejącego obiektu synchronizacji, który nie jest semafora, konstrukcji zakończy się niepowodzeniem.  
  
 *lpsaAttributes*  
 Atrybuty zabezpieczeń dla obiektu semafora. Pełny opis tej struktury, zobacz [SECURITY_ATTRIBUTES](http://msdn.microsoft.com/library/windows/desktop/aa379560) w zestawie Windows SDK.  
  
### <a name="remarks"></a>Uwagi  
 Dostęp, lub zwolnij `CSemaphore` obiektów, Utwórz [CMultiLock](../../mfc/reference/cmultilock-class.md) lub [CSingleLock](../../mfc/reference/csinglelock-class.md) obiekt i wywołanie jego [blokady](../../mfc/reference/csinglelock-class.md#lock) i [Unlock](../../mfc/reference/csinglelock-class.md#unlock) Funkcje elementów członkowskich.  
  
> [!IMPORTANT]
>  Po utworzeniu `CSemaphore` obiektów, użyj [GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360) aby upewnić się, że obiektu mutex nie już istnieje. Nieoczekiwanie istniał obiektu mutex, może oznaczać nieautoryzowanego zajmowanie i procesu może zamierza użyć obiektu mutex złośliwie. W takim przypadku zalecaną procedurą zabezpieczenia jest zamknąć dojścia i kontynuować tak, jakby wystąpił błąd podczas tworzenia obiektu.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa CSyncObject](../../mfc/reference/csyncobject-class.md)   
 [Wykres hierarchii](../../mfc/hierarchy-chart.md)



