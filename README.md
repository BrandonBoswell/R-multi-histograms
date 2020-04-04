# R-multi-histograms
#the R code for multiple histograms


setwd("C:/Users/Boswell/OneDrive - University of Houston-Clear Lake/Data Xfer Bckup/Spring 2020/ODrvStat5531Given/")
turtle <-     read.csv("Stat5531DataSets\\Stat5531Test1data.txt", header = T, col.names = c("x1","x2","x3","gender"), sep = "")
turtle2 <-     read.csv("Stat5531DataSets\\Stat5531Test1data.txt", header = T, sep = "")
setwd("D:\\Spring 2020\\Stat5531HW")
turtle$gender <-factor(turtle$gender)
turtle2$Gender <-factor(turtle2$Gender)

par(mfrow=c(1,3))
plot_multi_histogram <- function(df, feature, label_column) {
  plt <- ggplot(df, aes(x=eval(parse(text=feature)), fill=eval(parse(text=label_column)))) +
    geom_histogram(alpha=0.7, position="identity", aes(y = ..density..), bins = 10, color="black") +
    geom_density(alpha=0.7) +
    geom_vline(aes(xintercept=mean(eval(parse(text=feature)))), color="black", linetype="dashed", size=1) +
    labs(x=feature, y = "Density")
  plt + guides(fill=guide_legend(title=label_column))
}

plot_multi_histogram(turtle2, 'Length', 'Gender')
plot_multi_histogram(turtle2, 'Width', 'Gender')
plot_multi_histogram(turtle2, 'Height', 'Gender')
