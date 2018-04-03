# black-forest-cake

manager <- c(1,2,3,4,5)

date <- c("10/24/08","10/28/08","10/1/08","10/12/08","5/1/09")

country <- c("US","US","UK","UK","UK")

gender <- c("M","F","F","M","F")

age <- c(32,45,25,39,99)

q1 <- c(5,3,3,3,2)

q2 <- c(4,5,5,3,2)

q3 <- c(5,2,5,4,1)

q4 <- c(5,5,5,NA,2)

q5 <- c(5,5,2,NA,1)

leadership <- data.frame(manager,date,country,gender,age,q1,q2,q3,q4,q5,stringsAsFactors = F)

leadership

leadership <- within(leadership,{
agecat <- NA
agecat[age>75] <- "Elder"
agecat[age<=75] <- "Middle Aged"
agecat[age<55] <- "Young"
})

leadership

age <- c(32,45,85,60,99)

leadership

leadership <- data.frame(manager,date,country,gender,age,q1,q2,q3,q4,q5,stringsAsFactors = F)

#设定种子后，随机生成的数字可重现。为伪随机数。
set.seed(1234)
runif(5)

library(MASS)
options(digits = 3)
set.seed(1234)
mean <- c(230.7,146.7,3.6)
sigma <- matrix(c(15360.8,6721.2,-47.1,6721.2,4700.9,-16.5,-47.1,-16.5,0.3),
                nrow = 3,ncol = 3)
mydata <- mvrnorm(500,mean,sigma)
mydata <- as.data.frame(mydata)
names(mydata) <- c("y","x1","x2")
dim(mydata)
head(mydata,10)

mydata <- matrix(rnorm(30),nrow = 6)
mydata
apply(mydata, MARGIN = 1, FUN = mean)
apply(mydata, MARGIN = 2, FUN = mean)
apply(mydata, MARGIN = 2, FUN = mean,trim=0.2)


options(digits = 2)
Student <- c("John Davis","Angela Williams","Bullwinkle Moose",
             "David Jones","Janice Markhammer","Cheryl Cushing",
             "Reuven Ytzrhak","Greg Knox","Joel England","Mary Rayburn")
Math <- c(502,600,412,358,495,512,410,625,573,522)
Science <- c(95,99,80,82,75,85,80,95,89,86)
English <- c(25,22,18,15,20,28,15,30,27,18)
roster <- data.frame(Student,Math,Science,English,stringsAsFactors = F)
z <- scale(roster[,2:4])
score <- apply(z, 1, mean)
y <- quantile(score,c(.8,.6,.4,.2))
roster$grade[score>=y[1]] <- "A"
roster$grade[score<y[1]&score>=y[2]] <- "B"
roster$grade[score<y[2]&score>=y[3]] <- "C"
roster$grade[score<y[3]&score>=y[4]] <- "D"
roster$grade[score<y[4]] <- "F"

name <- strsplit(roster$Student," ")
lastname <- sapply(name, "[",2)
firstname <- sapply(name, "[",1)
roster <- cbind(firstname,lastname,roster[,-1])

roster <- roster[order(lastname,firstname),]

feelings <- c("sad","afraid")
for (i in feelings) print(switch(
  i,
  happy="I am glad U R happy",
  afraid="There is nothing to fear",
  sad="Cheer up",
  angry="Clam down now"
))
  


leadership

leadership <- within(leadership,{
agecat <- NA
agecat[age>75] <- "Elder"
agecat[age<=75] <- "Middle Aged"
agecat[age<55] <- "Young"
})

leadership

rename(leadership,c(manager="managerID",date="testDate"))

install.packages("reshape")

library(reshape)

rename(leadership,c(manager="managerID",date="testDate"))#rename函数需要调取reshape包，reshape包为非默认包，先安装，后library

合并函数功能cbind&merge,区别，merge根据索引列进行合并。
