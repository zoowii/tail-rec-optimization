#lang racket

;; 这里是示例代码，这段代码在Scheme中是可以执行的，因为Scheme标准规定了需要尾递归优化
;; 而对应的JavaScript代码是无法运行的，因为没有做尾递归优化，很快就超过最大调用深度了
(define (foo n)
 (if (> n 20140000)
    (begin
      (display "foo")
       n)
    (bar (+ n 1))))
(define (bar n)
  (if (> n 20130000)
     (begin
        (display "bar")
         n)
     (foo (+ n 2))))
(display (foo 1234))

;; 下面开始实际程序
(define call/cc call-with-current-continuation)

;; 这里是上面的示例代码，program就是实际使用中的程序代码（宏展开后）
(define program '((define (foo n)
 (if (> n 20140000)
    (begin
      (display "foo")
       n)
    (bar (+ n 1))))
(define (bar n)
  (if (> n 20130000)
     (begin
        (display "bar")
         n)
     (foo (+ n 2))))
(foo 1234) ; 这里没有加上display，是为了方便程序找到这个需要尾递归优化的函数foo
  ))

(define (id form)
  ;; 辅助函数，一个返回参数自身的函数
  form)

(define (procedure-definition? form)
  ;; 判断一个form是不是一个函数定义
  (if (and (list? form)
           (> (length form) 2)
           (eq? (car form) 'define)
           (list? (cadr form))
           (> (length (cadr form)) 1)
           )
      #t
      #f))

(define (find-procedure-definitions program)
  ;; 找到一段程序中所有的函数定义的名称
  (filter id
          (map (lambda (form)
                 (if (procedure-definition? form)
                     (caadr form)
                     #f))
               program)))

(define (find-func-calls program)
  ;; 找到一段程序中除了函数定义之外的函数调用，比如(foo 1234)
  (filter id
          (map (lambda (form)
                 (if (procedure-definition? form)
                     #f
                     form)) program))
  )

(define (find-tail-rec program)
  ;; 找到一段程序中的所有尾递归
  ;; TODO: 目前为了简单起见，而且demo代码中顶层只有一个函数调用(foo 1234)。所以只考虑最后一个函数调用，作为要判断尾递归优化的目标
  "hello")
