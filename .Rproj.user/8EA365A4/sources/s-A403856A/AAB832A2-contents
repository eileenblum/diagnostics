library(ggfortify)
library(tidyverse)

my_cars_data <- read_csv("./data/mydata.csv")

glimpse(my_cars_data)
summary(my_cars_data)
head(my_cars_data)

mod1 <- lm(mpg ~ wt, data = mtcars)
summary(mod1)

#1. The regression model is linear in parameters
#Eyeball it
mtcars %>%
  ggplot(., aes(x = wt, y = mpg)) +
  geom_point() +
  geom_smooth(method = lm, formula = y ~ poly(x, 2))

#2. The mean of residuals is zero
#Check model summary and test manually
mean(mod1$residuals)
summary(mod1)

#3. Homoskedasticity of residuals or equal variance
#left side plots
autoplot(mod1, which =c(1, 3))

#4. No autocorrelation of residuals
acf(mod1$residuals) #visual inspection
lmtest::dwtest(mod1) #formal test: Durbin-Watson test

#6 Normality of residuals
autoplot(mod1, which = 2)

autoplot(mod1)

#save a dataset as .csv
write_csv(x = mtcars, path = "./data/mydata.csv")