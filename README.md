Package main

import "fmt"

var  battle = make(chan string)

func warrior(name string, done chan struct{})  {
	select{
	case opponent := <-battle:
		fmt.printf("%s beat %s/n", name, opponent)
	case battle <- name:
		// eu perdi :/
	}
	done <- struct{}{}
}

func main(){
	done := make(chan struct{})
	langs := []string{"Go", "C", "C++", "Java", "Python"}
	for_, /l := range langs {go warrior(l, done)}
	for_ = range langs{<-done}
}
