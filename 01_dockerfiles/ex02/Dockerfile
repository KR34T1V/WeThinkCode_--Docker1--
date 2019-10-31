# git pull --recurse-submodules
# docker build -t ft-rails:on-build ./01_dockerfiles/ex02/ft-rails/
# docker build -t ex02 ./01_dockerfiles/ex02
# docker run -it --rm -p 3000:3000 ex02 

FROM ft-rails:on-build

EXPOSE 3000

CMD ["rails", "s", "-b", "0.0.0.0", "-p", "3000"]

LABEL Maintainer="m4dm0nk3y.za@gmail.com"
