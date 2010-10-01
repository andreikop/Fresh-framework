TARGET = fresh.so
OFILES = sipfreshcmodule.o sipfreshpDockWidgetTitleBar.o sipfreshpDockWidget.o sipfreshpActionsManager.o sipfreshpGroupPath.o sipfreshpDockToolBar.o sipfreshpDockToolBarManager.o sipfreshpMenuBar.o sipfreshpMainWindow.o sipfreshpSettings.o
HFILES = sipAPIfresh.h 

CC = gcc
CXX = g++
LINK = g++
CPPFLAGS = -DNDEBUG -DQT_NO_DEBUG -DQT_CORE_LIB -DQT_GUI_LIB -I. -I.. -I/usr/include/qt4 -I/usr/include/python2.6 -I/usr/share/qt4/mkspecs/default -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/X11R6/include
CFLAGS = -pipe -fPIC -O2 -fno-optimize-sibling-calls -Wall -W -D_REENTRANT
CXXFLAGS = -pipe -fPIC -O2 -fno-optimize-sibling-calls -fno-optimize-sibling-calls -Wall -W -D_REENTRANT
LFLAGS = -shared -Wl,-O1 -Wl,-rpath,/usr/lib -Wl,--version-script=fresh.exp
LIBS = -L/usr/lib -L../build -L/usr/X11R6/lib -lcppfresh -lQtCore -lQtGui -lXext -lX11 -lm -lpthread
MOC = /usr/bin/moc-qt4
.SUFFIXES: .c .o .cpp .cc .cxx .C


.cpp.o:
	$(CXX) -c $(CXXFLAGS) $(CPPFLAGS) -o $@ $<

.cc.o:
	$(CXX) -c $(CXXFLAGS) $(CPPFLAGS) -o $@ $<

.cxx.o:
	$(CXX) -c $(CXXFLAGS) $(CPPFLAGS) -o $@ $<

.C.o:
	$(CXX) -c $(CXXFLAGS) $(CPPFLAGS) -o $@ $<

.c.o:
	$(CC) -c $(CFLAGS) $(CPPFLAGS) -o $@ $<

all: $(TARGET)

$(OFILES): $(HFILES)

$(TARGET): $(OFILES)
	@echo '{ global: initfresh; local: *; };' > fresh.exp
	$(LINK) $(LFLAGS) -o $(TARGET) $(OFILES) $(LIBS)

install: $(TARGET)
	@test -d $(DESTDIR)/usr/lib/python2.6/dist-packages/PyQt4 || mkdir -p $(DESTDIR)/usr/lib/python2.6/dist-packages/PyQt4
	cp -f $(TARGET) $(DESTDIR)/usr/lib/python2.6/dist-packages/PyQt4/$(TARGET)
	strip $(DESTDIR)/usr/lib/python2.6/dist-packages/PyQt4/$(TARGET)
	@test -d $(DESTDIR)/usr/share/sip/PyQt4/fresh || mkdir -p $(DESTDIR)/usr/share/sip/PyQt4/fresh
	cp -f sip/pSettings.sip $(DESTDIR)/usr/share/sip/PyQt4/fresh/pSettings.sip
	cp -f sip/QSingleton.sip $(DESTDIR)/usr/share/sip/PyQt4/fresh/QSingleton.sip
	cp -f sip/pDockToolBarManager.sip $(DESTDIR)/usr/share/sip/PyQt4/fresh/pDockToolBarManager.sip
	cp -f sip/pDockWidget.sip $(DESTDIR)/usr/share/sip/PyQt4/fresh/pDockWidget.sip
	cp -f sip/pActionsManager.sip $(DESTDIR)/usr/share/sip/PyQt4/fresh/pActionsManager.sip
	cp -f sip/pDockWidgetTitleBar.sip $(DESTDIR)/usr/share/sip/PyQt4/fresh/pDockWidgetTitleBar.sip
	cp -f sip/pMenuBar.sip $(DESTDIR)/usr/share/sip/PyQt4/fresh/pMenuBar.sip
	cp -f sip/fresh.sip $(DESTDIR)/usr/share/sip/PyQt4/fresh/fresh.sip
	cp -f sip/pMainWindow.sip $(DESTDIR)/usr/share/sip/PyQt4/fresh/pMainWindow.sip
	cp -f sip/pDockToolBar.sip $(DESTDIR)/usr/share/sip/PyQt4/fresh/pDockToolBar.sip
	cp -f sip/pWorkspace.sip $(DESTDIR)/usr/share/sip/PyQt4/fresh/pWorkspace.sip
	cp -f sip/pGroupPath.sip $(DESTDIR)/usr/share/sip/PyQt4/fresh/pGroupPath.sip
	@test -d $(DESTDIR)/usr/share/qt4/fresh/api/python || mkdir -p $(DESTDIR)/usr/share/qt4/fresh/api/python
	cp -f fresh.api $(DESTDIR)/usr/share/qt4/fresh/api/python/fresh.api

clean:
	-rm -f $(TARGET)
	-rm -f sipfreshcmodule.o
	-rm -f sipfreshpDockWidgetTitleBar.o
	-rm -f sipfreshpDockWidget.o
	-rm -f sipfreshpActionsManager.o
	-rm -f sipfreshpGroupPath.o
	-rm -f sipfreshpDockToolBar.o
	-rm -f sipfreshpDockToolBarManager.o
	-rm -f sipfreshpMenuBar.o
	-rm -f sipfreshpMainWindow.o
	-rm -f sipfreshpSettings.o
	-rm -f fresh.exp
