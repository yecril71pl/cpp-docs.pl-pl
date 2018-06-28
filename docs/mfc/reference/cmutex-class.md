---
title: Klasa CMutex | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMutex
- AFXMT/CMutex
- AFXMT/CMutex::CMutex
dev_langs:
- C++
helpviewer_keywords:
- CMutex [MFC], CMutex
ms.assetid: 6330c050-4f01-4195-a099-2029b92f8cf1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f3bde85e64fe8593ec2637e767e8c3c70d3b8200
ms.sourcegitcommit: f1b051abb1de3fe96350be0563aaf4e960da13c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/27/2018
ms.locfileid: "37038080"
---
# <a name="cmutex-class"></a>Klasa CMutex
Reprezentuje "mutex" — obiektu synchronizacji, umożliwiająca jeden wątek wykluczają się wzajemnie dostęp do zasobu.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CMutex : public CSyncObject  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CMutex::CMutex](#cmutex)|Konstruuje `CMutex` obiektu.|  
  
## <a name="remarks"></a>Uwagi  
 Muteksy są przydatne, jeśli tylko jeden wątek jednocześnie można mogą modyfikować dane i kontrolowane zasobów. Na przykład dodawania węzłów do połączonej listy jest procesem, powinien być dozwolony tylko przez jeden wątek na raz. Za pomocą `CMutex` obiekt do kontrolowania listy połączonej, tylko jeden wątek jednocześnie uzyskać dostęp do listy.  
  
 Aby użyć `CMutex` obiektów, utworzyć `CMutex` obiektu, gdy potrzebny jest. Określ nazwę obiektu mutex czekać, a aplikacji należy początkowo jest jej właścicielem. Po powrocie z konstruktora access obiektu mutex. Wywołanie [CSyncObject::Unlock](../../mfc/reference/csyncobject-class.md#unlock) po zakończeniu dostępu do kontrolowanego zasobu.  
  
 Alternatywna metoda przy użyciu `CMutex` obiektów jest dodanie do zmiennej typu `CMutex` jako element członkowski danych klasy do formantu. Podczas konstruowania obiektu kontrolowanego, należy wywołać konstruktora z `CMutex` element członkowski danych, jeśli obiektu mutex jest początkowo własność, nazwa obiektu mutex (jeśli będzie on używany przez granice procesu) i potrzeby atrybutów zabezpieczeń.  
  
 Dostęp do zasobów kontrolowane przez `CMutex` obiektów w ten sposób, najpierw Utwórz zmienną obu typów [CSingleLock](../../mfc/reference/csinglelock-class.md) lub typ [CMultiLock](../../mfc/reference/cmultilock-class.md) w funkcji członkowskiej dostępu do tego zasobu. Następnie wywołaj zablokować obiektu `Lock` funkcji członkowskiej (na przykład [CSingleLock::Lock](../../mfc/reference/csinglelock-class.md#lock)). W tym momencie z wątku zostanie albo uzyskać dostęp do zasobu, poczekaj zasobu zwolnione i uzyskać dostęp lub zaczekaj zasobów do zwolnienia i limit czasu, można uzyskać dostęp do zasobu. W każdym przypadku zasobu uzyskaniu w sposób wątkowo. Aby zwolnić zasobu, użyj obiektu blokady `Unlock` funkcji członkowskiej (na przykład [CSingleLock::Unlock](../../mfc/reference/csinglelock-class.md#unlock)), lub zezwala na wykraczać poza zakres obiektu blokady.  
  
 Aby uzyskać więcej informacji na temat używania `CMutex` obiektów, zobacz artykuł [Multithreading: jak używać klas synchronizacji](../../parallel/multithreading-how-to-use-the-synchronization-classes.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CSyncObject](../../mfc/reference/csyncobject-class.md)  
  
 `CMutex`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxmt.h  
  
##  <a name="cmutex"></a>  CMutex::CMutex  
 Konstruuje nazwane i nienazwane `CMutex` obiektu.  
  
```  
CMutex(
    BOOL bInitiallyOwn = FALSE,  
    LPCTSTR lpszName = NULL,  
    LPSECURITY_ATTRIBUTES lpsaAttribute = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 *bInitiallyOwn*  
 Określa, czy tworzenie wątku `CMutex` obiektu początkowo ma dostęp do zasobów kontrolowane przez obiektu mutex.  
  
 *lpszName*  
 Nazwa `CMutex` obiektu. Jeśli istnieje innego obiektu mutex o takiej samej nazwie, *lpszName* musi być dostarczona, jeśli obiekt będzie można użyć poza granicami procesu. Jeśli **NULL**, obiektu mutex nie będą mieć nazwy. Jeśli nazwa pasuje do istniejącego obiektu mutex, konstruktora tworzy nową `CMutex` obiektu, który odwołuje się do obiektu mutex o tej nazwie. Jeśli nazwa jest zgodna z istniejącym obiektem synchronizacji nie jest obiektu mutex, konstrukcji zakończy się niepowodzeniem.  
  
 *lpsaAttribute*  
 Atrybuty zabezpieczeń dla obiektu mutex. Pełny opis tej struktury, zobacz [SECURITY_ATTRIBUTES](http://msdn.microsoft.com/library/windows/desktop/aa379560) w zestawie Windows SDK.  
  
### <a name="remarks"></a>Uwagi  
 Dostęp, lub zwolnij `CMutex` obiektów, Utwórz [CMultiLock](../../mfc/reference/cmultilock-class.md) lub [CSingleLock](../../mfc/reference/csinglelock-class.md) obiekt i wywołanie jego [blokady](../../mfc/reference/csinglelock-class.md#lock) i [Unlock](../../mfc/reference/csinglelock-class.md#unlock) Funkcje elementów członkowskich. Jeśli `CMutex` obiekt jest używany autonomiczny, wywołaj jego `Unlock` funkcji członkowskiej do jego zwolnienia.  
  
> [!IMPORTANT]
>  Po utworzeniu `CMutex` obiektów, użyj [GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360) aby upewnić się, że obiektu mutex nie już istnieje. Nieoczekiwanie istniał obiektu mutex, może oznaczać nieautoryzowanego zajmowanie i procesu może zamierza użyć obiektu mutex złośliwie. W takim przypadku zalecaną procedurą zabezpieczenia jest zamknąć dojścia i kontynuować tak, jakby wystąpił błąd podczas tworzenia obiektu.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa CSyncObject](../../mfc/reference/csyncobject-class.md)   
 [Wykres hierarchii](../../mfc/hierarchy-chart.md)



