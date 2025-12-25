FROM kotope/eink-art-gallery:0.0.3

USER root

# Create the wrapper script
RUN echo '#!/bin/bash' > /run_wrapper.sh && \
    echo 'mkdir -p /share/eink_art/images' >> /run_wrapper.sh && \
    echo 'mkdir -p /data/eink_art' >> /run_wrapper.sh && \
    echo 'ln -sf /share/eink_art/images /data/eink_art/images' >> /run_wrapper.sh && \
    echo 'exec python3 /app/app.py' >> /run_wrapper.sh && \
    chmod +x /run_wrapper.sh

CMD ["/run_wrapper.sh"]

