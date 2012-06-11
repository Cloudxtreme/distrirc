CXX=g++ -g
RM=del /F
CFLAGS=-Wall -W -Wall -Wextra -I"." -I".."

.PHONY: all test clean

all: test

test: runtests.exe
	runtests.exe

# Linking
runtests.exe: runtests.o LineConnection.o IRCServer.o tests/test_LineConnection.o
	$(CXX) $(CFLAGS) $^ -o $@ -lcppunit -L.. -lsockets -lws2_32

# Compile a .cpp into a .o
%.o: %.cpp
	$(CXX) -c $(CFLAGS) $< -o $@

# Clean up object files
clean:
	$(RM) *.o


runtests.o: runtests.cpp
LineConnection.o: LineConnection.cpp LineConnection.h ../sockets/Socket.h
IRCServer.o: IRCServer.cpp IRCServer.h ../sockets/Socket.h \
 LineConnection.h
test_LineConnection.o: tests/test_LineConnection.cpp LineConnection.h \
 ../sockets/Socket.h